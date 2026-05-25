# 🛒 Amazon Competitor Analysis Skill

> **AI-powered deep-dive competitor research for Amazon global marketplaces**  
> Covering all Amazon sites · All product categories · Full lifecycle support

[![Version](https://img.shields.io/badge/version-1.1-blue.svg)](CHANGELOG.md)
[![License](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)
[![Platform](https://img.shields.io/badge/platform-QClaw%20%7C%20OpenClaw-orange.svg)](#)

---

## 📖 Overview

**Amazon Competitor Analysis** is a comprehensive AI skill designed for Amazon sellers who need deep, structured intelligence on their competitors' marketing playbooks. Built for the QClaw/OpenClaw agent ecosystem, it systematically dissects any Amazon product across **7 core analysis modules** — from basic info to actionable strategy blueprints.

Whether you're launching a new product, optimizing your ad spend, or planning global expansion, this skill delivers **standardized competitor reports and differentiated promotion strategies** in hours, not days.

### 🎯 Who Is This For?

- Amazon sellers analyzing competitor promotion tactics
- New product launch teams conducting pre-launch competitor research
- Ad managers optimizing and reviewing campaign performance
- Category managers running multi-competitor benchmarking
- Market entry strategists tailoring approaches per Amazon marketplace

---

## ✨ Features

### 7 Core Analysis Modules

| # | Module | What It Covers |
|---|--------|---------------|
| 1 | **Basic Info** | Brand, ASIN, price, rating, sales volume, BSR, conversion rate, variants |
| 2 | **Traffic Structure** | Organic vs. paid split → search vs. recommendation → granular tag-level breakdown |
| 3 | **Ad Strategy** | SP/SB/SBV/SD/SDV across 5 ad types — keyword distribution, defense/offense tactics |
| 4 | **Promotion Strategy** | 90-day Keepa price history → coupon/deal/discount/mega-sale patterns |
| 5 | **Creative Assets** | Image & video analysis by placement → content structure → reusable templates |
| 6 | **Off-site Traffic** | Website + Deal sites + YouTube/Facebook/TikTok → channel effectiveness |
| 7 | **SWOT & Action Plan** | Multi-dimension comparison → differentiation strategy → monthly execution checklist |

### 🌍 Global Marketplace Support

| Region | Marketplaces |
|--------|-------------|
| **Americas** | US, Canada, Mexico, Brazil |
| **Europe** | UK, Germany, France, Italy, Spain, Netherlands, Sweden, Poland, Belgium, Turkey |
| **Asia-Pacific** | Japan, Australia, Singapore, India |
| **Middle East** | UAE, Saudi Arabia |
| **Southeast Asia** | Singapore, Thailand, Vietnam |

### ⚡ Flexible Workflows

| Workflow | Time | Modules Used |
|----------|------|-------------|
| **Quick Survey** | ~30 min | Module 1 (Basic) + 3 (Ads) + 4 (Promos) |
| **Deep Research** | 2–4 hrs | All 7 modules → full report |
| **Multi-Competitor** | ~1 hr per competitor | Per-competitor info cards → merged SWOT |

---

## 🚀 Installation

### Prerequisites

- [QClaw](https://github.com/qclaw) or [OpenClaw](https://github.com/openclaw) agent runtime
- **Required tools** (subscriptions needed):
  - [Seller Sprite](https://www.sellersprite.com) or [Helium 10](https://www.helium10.com) — sales, traffic, ad data
  - [Keepa](https://keepa.com) — price history, promotion records
  - [SimilarWeb](https://www.similarweb.com) — off-site traffic sources
  - Amazon frontend access — listings, creatives, related placements

### Install via SkillHub (Recommended)

```bash
skillhub install amazon-competitor-analysis
```

### Manual Installation

```bash
# Clone or copy into your skills directory
cp -r amazon-competitor-analysis ~/.qclaw/skills/
```

---

## 🏃 Quick Start

```
@amazon-competitor-analysis
Analyze competitor ASIN B0XXXXXXXX on Amazon US:
- My product: [category + key selling points + price range]
- Competitor ASINs: B0XXX1, B0XXX2, B0XXX3
- Mode: deep research (all 7 modules)
```

See [references/quick-start.md](references/quick-start.md) for the 30-minute rapid survey workflow.

---

## 📋 Usage Examples

### Example 1: Quick Survey (30 min)

```
@amazon-competitor-analysis
Quick survey mode: ASIN B0ABCDEFGH on Amazon DE
My product: smart pet feeder, app-control, 49-69 EUR
```

### Example 2: Full Deep Research

```
@amazon-competitor-analysis
Deep research: B0XXXXXX on Amazon JP
My product: matcha tea set, ceramic, 3000-5000 JPY
Include all 7 modules, 90-day analysis window
```

### Example 3: Multi-Competitor Comparison

```
@amazon-competitor-analysis
Compare: B0AAA, B0BBB, B0CCC on Amazon US
My product: portable power station, 1000W, $499-699
Output: merged SWOT + differentiation strategy
```

See [examples/](examples/) for fully worked-out examples with expected outputs.

---

## 📁 Project Structure

```
amazon-competitor-analysis/
├── SKILL.md                    # Skill definition & core logic
├── README.md                   # You are here
├── CHANGELOG.md                # Version history
├── CONTRIBUTING.md             # How to contribute
├── LICENSE                     # MIT License
├── .gitignore
├── docs/
│   └── SKILL_DOCUMENTATION.md  # Full API & module reference
├── examples/
│   ├── quick-survey-example.md
│   ├── deep-research-example.md
│   └── multi-competitor-comparison.md
├── templates/
│   └── blank-research-template.md  # Fillable research template
└── references/
    ├── modules.md               # 7-module complete output templates
    ├── site-guide.md            # Marketplace-specific adaptation guide
    └── quick-start.md           # 30-minute quick survey workflow
```

---

## 🔧 Dependencies

### Data Tools (Required)

| Tool | Purpose | Free Tier? |
|------|---------|-----------|
| **Seller Sprite** / **Helium 10** | Sales estimates, traffic data, keyword research | Limited free tier |
| **Keepa** | Price history charts, promotion tracking | Limited free tier |
| **SimilarWeb** | Website traffic analysis, referral sources | Limited free tier |
| **Amazon Frontend** | Listing content, creative assets, related product placement | Free |

### Optional Tools

- **Social Blade** — YouTube/social media follower & engagement data

---

## 🤝 Contributing

We welcome contributions! See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

Areas we'd especially love help with:

- Additional marketplace adapters (India, Mexico, Australia, etc.)
- New analysis modules (review sentiment, A+ content deep-dive, etc.)
- Template improvements and localization
- Integration with additional data tools (Jungle Scout, Viral Launch, etc.)

---

## 📜 License

MIT License — see [LICENSE](LICENSE) for details.

---

## 🙏 Acknowledgments

- Built for the [QClaw / OpenClaw](https://github.com/openclaw) agent ecosystem
- Inspired by real Amazon seller workflows and the need for structured, reusable competitor intelligence
- Data tools referenced are trademarks of their respective owners

---

**⭐ If this skill helps your Amazon business, give it a star!**
