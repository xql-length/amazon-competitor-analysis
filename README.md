# 馃洅 Amazon Competitor Analysis Skill

> **AI-powered deep-dive competitor research for Amazon global marketplaces**  
> Covering all Amazon sites 路 All product categories 路 Full lifecycle support

[![Version](https://img.shields.io/badge/version-1.1-blue.svg)](CHANGELOG.md)
[![License](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)
[![Platform](https://img.shields.io/badge/platform-QClaw%20%7C%20OpenClaw-orange.svg)](#)

---

## 馃摉 Overview

**Amazon Competitor Analysis** is a comprehensive AI skill designed for Amazon sellers who need deep, structured intelligence on their competitors' marketing playbooks. Built for the QClaw/OpenClaw agent ecosystem, it systematically dissects any Amazon product across **7 core analysis modules** 鈥?from basic info to actionable strategy blueprints.

Whether you're launching a new product, optimizing your ad spend, or planning global expansion, this skill delivers **standardized competitor reports and differentiated promotion strategies** in hours, not days.

### 馃幆 Who Is This For?

- Amazon sellers analyzing competitor promotion tactics
- New product launch teams conducting pre-launch competitor research
- Ad managers optimizing and reviewing campaign performance
- Category managers running multi-competitor benchmarking
- Market entry strategists tailoring approaches per Amazon marketplace

---

## 鉁?Features

### 7 Core Analysis Modules

| # | Module | What It Covers |
|---|--------|---------------|
| 1 | **Basic Info** | Brand, ASIN, price, rating, sales volume, BSR, conversion rate, variants |
| 2 | **Traffic Structure** | Organic vs. paid split 鈫?search vs. recommendation 鈫?granular tag-level breakdown |
| 3 | **Ad Strategy** | SP/SB/SBV/SD/SDV across 5 ad types 鈥?keyword distribution, defense/offense tactics |
| 4 | **Promotion Strategy** | 90-day Keepa price history 鈫?coupon/deal/discount/mega-sale patterns |
| 5 | **Creative Assets** | Image & video analysis by placement 鈫?content structure 鈫?reusable templates |
| 6 | **Off-site Traffic** | Website + Deal sites + YouTube/Facebook/TikTok 鈫?channel effectiveness |
| 7 | **SWOT & Action Plan** | Multi-dimension comparison 鈫?differentiation strategy 鈫?monthly execution checklist |

### 馃實 Global Marketplace Support

| Region | Marketplaces |
|--------|-------------|
| **Americas** | US, Canada, Mexico, Brazil |
| **Europe** | UK, Germany, France, Italy, Spain, Netherlands, Sweden, Poland, Belgium, Turkey |
| **Asia-Pacific** | Japan, Australia, Singapore, India |
| **Middle East** | UAE, Saudi Arabia |
| **Southeast Asia** | Singapore, Thailand, Vietnam |

### 鈿?Flexible Workflows

| Workflow | Time | Modules Used |
|----------|------|-------------|
| **Quick Survey** | ~30 min | Module 1 (Basic) + 3 (Ads) + 4 (Promos) |
| **Deep Research** | 2鈥? hrs | All 7 modules 鈫?full report |
| **Multi-Competitor** | ~1 hr per competitor | Per-competitor info cards 鈫?merged SWOT |

---

## 馃殌 Installation

### Prerequisites

- [QClaw](https://github.com/qclaw) or [OpenClaw](https://github.com/openclaw) agent runtime
- **Required tools** (subscriptions needed):
  - [Seller Sprite](https://www.sellersprite.com) or [Helium 10](https://www.helium10.com) 鈥?sales, traffic, ad data
  - [Keepa](https://keepa.com) 鈥?price history, promotion records
  - [SimilarWeb](https://www.similarweb.com) 鈥?off-site traffic sources
  - Amazon frontend access 鈥?listings, creatives, related placements

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

## 馃弮 Quick Start

```
@amazon-competitor-analysis
Analyze competitor ASIN B0XXXXXXXX on Amazon US:
- My product: [category + key selling points + price range]
- Competitor ASINs: B0XXX1, B0XXX2, B0XXX3
- Mode: deep research (all 7 modules)
```

See [references/quick-start.md](references/quick-start.md) for the 30-minute rapid survey workflow.

---

## 馃搵 Usage Examples

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

## 馃搧 Project Structure

```
amazon-competitor-analysis/
鈹溾攢鈹€ SKILL.md                    # Skill definition & core logic
鈹溾攢鈹€ README.md                   # You are here
鈹溾攢鈹€ CHANGELOG.md                # Version history
鈹溾攢鈹€ CONTRIBUTING.md             # How to contribute
鈹溾攢鈹€ LICENSE                     # MIT License
鈹溾攢鈹€ .gitignore
鈹溾攢鈹€ docs/
鈹?  鈹斺攢鈹€ SKILL_DOCUMENTATION.md  # Full API & module reference
鈹溾攢鈹€ examples/
鈹?  鈹溾攢鈹€ quick-survey-example.md
鈹?  鈹溾攢鈹€ deep-research-example.md
鈹?  鈹斺攢鈹€ multi-competitor-comparison.md
鈹溾攢鈹€ templates/
鈹?  鈹斺攢鈹€ blank-research-template.md  # Fillable research template
鈹斺攢鈹€ references/
    鈹溾攢鈹€ modules.md               # 7-module complete output templates
    鈹溾攢鈹€ site-guide.md            # Marketplace-specific adaptation guide
    鈹斺攢鈹€ quick-start.md           # 30-minute quick survey workflow
```

---

## 馃敡 Dependencies

### Data Tools (Required)

| Tool | Purpose | Free Tier? |
|------|---------|-----------|
| **Seller Sprite** / **Helium 10** | Sales estimates, traffic data, keyword research | Limited free tier |
| **Keepa** | Price history charts, promotion tracking | Limited free tier |
| **SimilarWeb** | Website traffic analysis, referral sources | Limited free tier |
| **Amazon Frontend** | Listing content, creative assets, related product placement | Free |

### Optional Tools

- **Social Blade** 鈥?YouTube/social media follower & engagement data

---

## 馃 Contributing

We welcome contributions! See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

Areas we'd especially love help with:

- Additional marketplace adapters (India, Mexico, Australia, etc.)
- New analysis modules (review sentiment, A+ content deep-dive, etc.)
- Template improvements and localization
- Integration with additional data tools (Jungle Scout, Viral Launch, etc.)

---

## 馃摐 License

MIT License 鈥?see [LICENSE](LICENSE) for details.

---

## 馃檹 Acknowledgments

- Built for the [QClaw / OpenClaw](https://github.com/openclaw) agent ecosystem
- Inspired by real Amazon seller workflows and the need for structured, reusable competitor intelligence
- Data tools referenced are trademarks of their respective owners

---

**猸?If this skill helps your Amazon business, give it a star!**