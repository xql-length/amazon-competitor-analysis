# Contributing to Amazon Competitor Analysis

Thank you for your interest in contributing! This document provides guidelines to help you make effective contributions.

## Table of Contents

- [Code of Conduct](#code-of-conduct)
- [How Can I Contribute?](#how-can-i-contribute)
- [Development Setup](#development-setup)
- [Pull Request Process](#pull-request-process)
- [Style Guidelines](#style-guidelines)
- [Adding a New Module](#adding-a-new-module)
- [Adding a New Marketplace Adapter](#adding-a-new-marketplace-adapter)

---

## Code of Conduct

This project adheres to a standard open-source code of conduct. By participating, you are expected to uphold a respectful and inclusive environment.

---

## How Can I Contribute?

### 馃悰 Reporting Bugs

Before submitting a bug report:
1. Check the [Issues](../../issues) to see if it's already reported
2. Search existing discussions

When submitting, include:
- **Environment**: QClaw/OpenClaw version, OS, skill version
- **Steps to reproduce**: Be specific and minimal
- **Expected vs actual behavior**
- **Screenshots** or logs if applicable

### 馃挕 Suggesting Enhancements

We especially welcome ideas for:
- **New analysis modules** (review sentiment, A+ content deep-dive, pricing elasticity, etc.)
- **Marketplace adapters** for uncovered regions (India, Australia, Mexico, Brazil, etc.)
- **Tool integrations** (Jungle Scout, Viral Launch, DataHawk, etc.)
- **Template improvements** and localization (German, Japanese, Arabic, etc.)
- **Performance optimizations** for the 7-module pipeline

### 馃摑 Documentation

Documentation improvements are always appreciated:
- Fix typos, clarify instructions
- Add translations
- Create video tutorials or walkthroughs

---

## Development Setup

### Prerequisites

- QClaw or OpenClaw agent runtime installed
- Access to at least one of: Seller Sprite, Helium 10 (for testing)
- Keepa and SimilarWeb accounts (for full testing)

### Setup Steps

```bash
# Clone the repository
git clone https://github.com/YOUR_USERNAME/amazon-competitor-analysis.git
cd amazon-competitor-analysis

# Install as a local skill
cp -r . ~/.qclaw/skills/amazon-competitor-analysis

# Verify it's loaded
# In your QClaw session, run: @amazon-competitor-analysis --help
```

### Project Structure

```
amazon-competitor-analysis/
鈹溾攢鈹€ SKILL.md                          # Skill definition (entry point)
鈹?  鈹溾攢鈹€ Core logic & workflow decision tree
鈹?  鈹溾攢鈹€ 7 module descriptions
鈹?  鈹斺攢鈹€ Site adaptation overview
鈹溾攢鈹€ references/
鈹?  鈹溾攢鈹€ modules.md                    # Complete output templates per module
鈹?  鈹溾攢鈹€ site-guide.md                 # Per-marketplace adaptation rules
鈹?  鈹斺攢鈹€ quick-start.md                # 30-minute rapid survey guide
鈹溾攢鈹€ assets/
鈹?  鈹斺攢鈹€ blank-template.md            # Fillable blank research template
鈹溾攢鈹€ templates/                        # Additional templates (empty by default)
鈹溾攢鈹€ examples/                         # Worked examples
鈹斺攢鈹€ docs/                             # Extended documentation
```

### Key Files to Modify

| What to change | File to edit |
|---------------|-------------|
| Module logic / workflow | `SKILL.md` |
| Module output templates | `references/modules.md` |
| Marketplace rules | `references/site-guide.md` |
| Quick survey guide | `references/quick-start.md` |
| Blank template | `assets/blank-template.md` |

---

## Pull Request Process

1. **Fork** the repository and create your branch from `main`
2. **Name your branch** descriptively: `feature/india-adapter`, `fix/keepa-parsing`, `docs/german-translation`
3. **Make your changes**, following the style guidelines below
4. **Test** your changes:
   - Run at least one full module with real ASIN data
   - Verify output format matches the existing template structure
   - Test edge cases (products with no reviews, new listings, etc.)
5. **Update documentation**:
   - If adding a module, update `SKILL.md` module list and `references/modules.md`
   - If adding a marketplace, update `SKILL.md` site table and `references/site-guide.md`
   - Update `CHANGELOG.md` under `[Unreleased]`
6. **Submit** a Pull Request with a clear description:
   - What problem does it solve?
   - What changes were made?
   - How was it tested?
   - Screenshots of output if relevant

### PR Review Checklist

Maintainers will check:
- [ ] Does it follow the module template structure?
- [ ] Are all table formats consistent with existing modules?
- [ ] Does it maintain backward compatibility?
- [ ] Is the documentation updated?
- [ ] Are marketplace-specific rules well-reasoned?

---

## Style Guidelines

### Module Output Templates

All module output templates in `references/modules.md` follow this structure:

```markdown
### Module N: [Module Name]

**Execution Steps:**
1. Step one
2. Step two

**Output Template:**
[Standardized table or format]

---
```

### Table Formats

Use consistent Markdown table formatting:

```markdown
| Column 1 | Column 2 | Column 3 |
|----------|----------|----------|
| Value    | Value    | Value    |
```

### Naming Conventions

- Module numbers: 1-7 (existing), 8+ for new modules
- Marketplace codes: Use standard Amazon marketplace codes (US, DE, JP, etc.)
- ASIN placeholders: `B0XXXXXXXX` for examples, `B0XXX1` etc. for comparisons

### Language

- Documentation: English
- Code comments: English
- Variable names: camelCase
- Marketplace-specific terms: Use local language where appropriate (e.g., "Prime Day" not "浼氬憳鏃?)

---

## Adding a New Module

To add a new analysis module (e.g., Module 8: Review Sentiment Analysis):

### 1. Update SKILL.md

Add the module to the main module list and workflow decision tree:

```markdown
### Module 8: Review Sentiment Analysis
Use [tool] to extract top positive/negative review themes -> sentiment score -> improvement priorities.
```

### 2. Create Output Template

Add to `references/modules.md`:

```markdown
---
### Module 8: Review Sentiment Analysis

**Execution Steps:**
1. Export all reviews from tool (Helium 10 Review Insights / Seller Sprite)
2. Identify top 10 positive themes and top 10 negative themes
3. Calculate sentiment ratio (positive / total)
4. Map negative themes to product improvement priorities

**Output Template:**

| Sentiment Metric | Value |
|-----------------|-------|
| Total Reviews | XXX |
| Positive % | XX% |
| Negative % | XX% |
| Top Positive Theme 1 | XXX |
| Top Negative Theme 1 | XXX |
| Improvement Priority 1 | XXX |
```

### 3. Update Documentation

- Add module to README module table
- Update `docs/SKILL_DOCUMENTATION.md`
- Add to `CHANGELOG.md`

---

## Adding a New Marketplace Adapter

To add support for a new marketplace (e.g., Amazon India):

### 1. Research Phase

Gather marketplace-specific data:
- Consumer behavior patterns
- Popular promotion types and frequencies
- Dominant social media platforms
- Unique regulatory requirements
- Local holidays and shopping festivals

### 2. Update site-guide.md

Add a new section following the existing template:

```markdown
---
## India (IN)

**Core Characteristics:** [Brief description of market]

| Adjustment Dimension | Specific Actions |
|---------------------|-----------------|
| [Dimension 1] | [Action details] |
| [Dimension 2] | [Action details] |
```

### 3. Update SKILL.md

Add the new marketplace to the site adaptation table.

### 4. Test

Run a full analysis on at least 3 products in the new marketplace to validate the adapter.

---

## Questions?

Feel free to open an issue with the `question` label, or reach out to the maintainers directly.

**Thank you for contributing! 馃帀**