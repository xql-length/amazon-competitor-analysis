# Skill Documentation — Amazon Competitor Analysis

> **Version:** 1.1  
> **Type:** QClaw/OpenClaw Agent Skill  
> **Category:** E-commerce / Market Research

---

## Table of Contents

1. [Architecture Overview](#architecture-overview)
2. [Input Parameters](#input-parameters)
3. [Workflow Decision Tree](#workflow-decision-tree)
4. [Module Reference](#module-reference)
5. [Site Adaptation Engine](#site-adaptation-engine)
6. [Output Format](#output-format)
7. [Tool Dependencies](#tool-dependencies)
8. [Error Handling](#error-handling)
9. [Performance & Optimization](#performance--optimization)

---

## Architecture Overview

```
User Request
    |
    v
┌───────────────────────────────────────┐
│         Parameter Parser               │
│  (ASIN, site, product, mode, period)   │
└───────────────────────────────────────┘
    |
    v
┌───────────────────────────────────────┐
│       Workflow Router                  │
│  Quick Survey / Deep / Multi-Compare   │
└───────────────────────────────────────┘
    |
    v
┌───────────────────────────────────────┐
│     Site Adaptation Engine             │
│  Applies marketplace-specific rules    │
└───────────────────────────────────────┘
    |
    v
┌───────────────────────────────────────┐
│     7-Module Pipeline (sequential)     │
│  Module 1 -> 2 -> 3 -> 4 -> 5 -> 6 -> 7│
└───────────────────────────────────────┘
    |
    v
┌───────────────────────────────────────┐
│       Report Compiler                  │
│  Markdown report + Action checklist    │
└───────────────────────────────────────┘
```

---

## Input Parameters

### Required Parameters

| Parameter | Type | Description | Example |
|-----------|------|-------------|---------|
| `target_site` | string | Amazon marketplace code | `US`, `DE`, `JP`, `AE` |
| `self_product` | object | Your product info | `{category: "pet feeder", selling_points: ["app control"], price_range: "$49-69"}` |
| `competitor_asins` | string[] | Competitor ASINs (3-5 recommended) | `["B0XXX1", "B0XXX2", "B0XXX3"]` |

### Optional Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `research_period` | string | `"30d_basic_90d_trend"` | Data window: `30d` / `90d` / `180d` / `1y` |
| `focus_modules` | int[] | `[1,2,3,4,5,6,7]` | Specific modules to run |
| `output_format` | string | `"markdown"` | Report format: `markdown` (only format currently supported) |
| `competitor_priority` | string | `"auto"` | Selection logic: `auto` (top BSR) / `manual` / `closest_price` |

### Selection Priority for Competitor ASINs

When `competitor_priority` is `auto`:
1. BSR top 10 within the category
2. Same price range (±30%)
3. Fastest growth in last 3 months

---

## Workflow Decision Tree

```
User Request Received
|
+-- Mode: "quick_survey" (~30 min)
|   |
|   +-- Run Module 1: Basic Info Card
|   +-- Run Module 3: Ad Strategy (keywords only)
|   +-- Run Module 4: Promotion Strategy (Keepa 90d)
|   +-- Output: Executive Summary
|
+-- Mode: "deep_research" (2-4 hours)
|   |
|   +-- Run all 7 modules sequentially
|   +-- Apply site adaptation rules
|   +-- Cross-reference module findings
|   +-- Output: Full Report + Action Checklist
|
+-- Mode: "multi_competitor" (~1h per competitor)
    |
    +-- For each ASIN:
    |   +-- Run Modules 1-6 independently
    +-- Merge all into Module 7:
        +-- Multi-competitor SWOT comparison
        +-- Differentiation strategy
        +-- Prioritized action plan
```

---

## Module Reference

### Module 1: Basic Info Research

**Purpose:** Establish baseline metrics for competitor benchmarking.

**Data Sources:**
- Amazon frontend (listing page)
- Seller Sprite / Helium 10 (sales estimates, conversion rate)

**Key Metrics Extracted:**
- Brand name, Core ASIN, Listing date
- Current price, Promotional price
- Rating, Total reviews, Recent review velocity
- Daily/Monthly sales volume
- BSR (main category + subcategory)
- Estimated conversion rate
- Variant count

**Output:** Standardized "Core Competitor Info Card" table (see `references/modules.md`).

---

### Module 2: Traffic Structure Decomposition

**Purpose:** Understand how competitor traffic is sourced and distributed.

**Three-Tier Analysis:**

```
Level 1: Organic vs. Paid Split
  |
  +-- Level 2: Search vs. Recommendation
        |
        +-- Level 3: Traffic Tag Breakdown
              |-- Trending Now
              |-- Highly Rated
              |-- Customers Frequently Viewed
              |-- Amazon's Choice
              |-- Sponsored Products Related
              +-- Variant-level traffic share
```

**Data Sources:** Seller Sprite / Helium 10 traffic analytics.

**Key Insight:** Identifies which traffic tags drive the most volume — reveals competitor's organic strength and recommendation engine positioning.

---

### Module 3: Ad Strategy Analysis

**Purpose:** Map the full advertising playbook across all Amazon ad types.

**5 Ad Types Analyzed:**

| Ad Type | Full Name | Key Dimensions |
|---------|-----------|---------------|
| SP | Sponsored Products | Keyword targeting, auto/manual campaigns |
| SB | Sponsored Brands | Brand store landing, product collection |
| SBV | Sponsored Brands Video | Video creative, storytelling approach |
| SD | Sponsored Display | Audience targeting, contextual targeting |
| SDV | Sponsored Display Video | Video + display retargeting |

**Keyword Distribution Analysis:**
- **Head terms** (top 100 search volume): Strategy for brand defense & category dominance
- **Mid-tail terms** (101-500): Balanced volume and conversion
- **Long-tail terms** (500+): High conversion, low competition

**Tactical Analysis:**
- **Defensive:** Competitor bidding on own brand terms, own ASIN targeting
- **Offensive:** Competitor bidding on competitor brand terms, category conquest

---

### Module 4: Promotion Strategy

**Purpose:** Decode pricing patterns and promotional rhythm.

**4 Promotion Types Tracked:**

| Type | Typical Discount | Frequency | Duration |
|------|-----------------|-----------|----------|
| Long-term Promo | 2-for-X, 3-for-Y, multi-buy | Always on | Year-round |
| Short-term Deal | 10-30% off | Bi-weekly to monthly | 7-14 days |
| Direct Price Cut | 5-15% cumulative | Quarterly | Permanent |
| Mega-sale Event | 20-50% off | Prime Day, BFCM | 3-7 days |

**Price Floor Analysis:**
- Historical lowest price
- Daily transaction price
- Mega-sale transaction price
- Price adjustment trajectory
- List price strategy (strikethrough pricing)

**Data Source:** Keepa 90-day price chart.

---

### Module 5: Creative Assets Breakdown

**Purpose:** Reverse-engineer competitor visual strategy.

**Priority Hierarchy (by conversion impact):**
```
Main Image Video > Related Video > A+ Video > Ad Video > Main Image > Secondary Images / A+ Content
```

**Video Analysis Framework:**
1. Opening 3 seconds: Pain point introduction
2. Middle section: Key selling points demonstrated (5-10 features)
3. Closing: Brand + Slogan + Call to action
4. Technical specs: Duration, aspect ratio (16:9), resolution (1920×1080)

**Image Analysis:**
- Content structure per position (main, secondary 1-7, A+ modules)
- Selling point display order
- Identifiable design patterns and templates

---

### Module 6: Off-site Traffic Research

**Purpose:** Map the full external traffic ecosystem.

**Channels Analyzed:**

| Channel | Key Metrics | Tool |
|---------|------------|------|
| Official Website | Monthly visits, traffic sources | SimilarWeb |
| Deal Sites | Posting frequency, heat score | Deal site browsing |
| YouTube | Subscribers, avg views, content type | Social Blade / Manual |
| Facebook | Followers, engagement rate | Manual |
| TikTok | Followers, avg likes | Manual |

**Promotion Cadence Mapping:**
- How external promotions sync with on-site deals
- Content calendar patterns
- Cross-channel coordination

---

### Module 7: SWOT Analysis & Action Plan

**Purpose:** Synthesize all findings into actionable strategy.

**8-Dimension Comparison Matrix:**

| Dimension | Competitor Strength | Competitor Weakness | Our Opportunity |
|-----------|-------------------|--------------------|----------------|
| Product Power | ... | ... | ... |
| Price Band | ... | ... | ... |
| Traffic Structure | ... | ... | ... |
| Ad Investment | ... | ... | ... |
| Promotion Strategy | ... | ... | ... |
| Creative Quality | ... | ... | ... |
| Off-site Presence | ... | ... | ... |
| Review Sentiment | ... | ... | ... |

**Monthly Action Checklist:**

Each action item includes:
- Task type (product/ad/promo/creative/off-site)
- Specific content
- Budget allocation
- Deadline
- Responsible person

---

## Site Adaptation Engine

The skill automatically adjusts analysis focus based on the target marketplace.

### Adaptation Rules per Region

**Americas/Europe:**
- Heavy emphasis on off-site traffic (YouTube, Deal sites)
- SD/SDV display ad analysis (higher share in these markets)
- Video creative weight is maximum
- Prime Day / BFCM mega-sale strategy tracking

**Japan:**
- Promotional frequency analysis (higher than Western markets)
- Detailed product image requirements
- List price strategy detection
- Review granularity analysis (packaging, instructions)
- Twitter/X and LINE social media focus

**Southeast Asia:**
- Logistics and delivery method comparison
- Price floor and discount limit analysis
- Low-price + variant upsell strategy detection

**Middle East:**
- Advertising intensity analysis
- COD (Cash on Delivery) availability tracking
- Arabic localization quality assessment
- Ramadan / White Friday promotional strategy

Full rules in `references/site-guide.md`.

---

## Output Format

### Standard Report Structure

```markdown
# [Site] [Competitor Brand] Comprehensive Research Report

> Research Date: YYYY.MM.DD
> Period: 30-day basic + 90-day trend
> Reference Product: [category + selling points + price range]
> Tools: Seller Sprite, Keepa, SimilarWeb

## 1. Core Competitor Basic Info
## 2. Traffic Structure Deep Dive
## 3. Ad Strategy Full Analysis
## 4. Promotion Strategy & Price Rhythm
## 5. Creative Assets & Reusable Templates
## 6. Off-site Traffic Channel Layout
## 7. SWOT Comparison & Action Plan
```

---

## Tool Dependencies

### Primary Tools

| Tool | Module Usage | Data Provided |
|------|-------------|---------------|
| **Seller Sprite / Helium 10** | 1, 2, 3 | Sales, traffic, keywords, ad data |
| **Keepa** | 4 | Price history, promotion timeline |
| **SimilarWeb** | 6 | Website traffic, referral sources |
| **Amazon Frontend** | 1, 5 | Listing content, creative assets |

### Fallback Strategy

If a tool is unavailable:
- **No Seller Sprite / Helium 10**: Mark modules 1-3 as "estimated" with visible caveats; use Amazon frontend for basic info only
- **No Keepa**: Skip Module 4 price history; use current price only
- **No SimilarWeb**: Skip website traffic in Module 6; rely on social media data

---

## Error Handling

### Common Issues & Resolutions

| Issue | Cause | Resolution |
|-------|-------|------------|
| "ASIN not found" | Invalid or de-listed ASIN | Verify ASIN on Amazon; request alternative |
| "No sales data" | Tool API limit or new listing | Use BSR-to-sales estimation formula |
| "Keepa data incomplete" | Product too new (<90 days) | Note in report; use available window |
| "No ad data" | Competitor not running ads | Note as strategic insight (organic-only strategy) |
| "SimilarWeb no data" | Low-traffic website | Skip; note "insufficient traffic" |

---

## Performance & Optimization

### Time Estimates

| Workflow | Expected Duration | Bottleneck |
|----------|------------------|------------|
| Quick Survey | 25-35 min | Tool data loading |
| Deep Research (single) | 2-4 hours | Manual data gathering + analysis |
| Multi-Competitor (3 ASINs) | 3-5 hours | Module 7 cross-referencing |

### Optimization Tips

1. **Batch ASIN lookups**: Query multiple ASINs simultaneously in Seller Sprite / H10
2. **Pre-load Keepa charts**: Open all competitor Keepa tabs at once
3. **Use templates**: Fill `assets/blank-template.md` while browsing to avoid rework
4. **Prioritize by module**: Start with Module 1, skip to 7 if you already know the category well
5. **Cache site rules**: Keep `references/site-guide.md` open for quick reference during analysis
