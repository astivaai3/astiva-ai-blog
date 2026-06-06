# Building Astiva AI: The Product Roadmap

<!-- canonical: https://astiva.ai/blog/astiva-product-roadmap-building-ai-visibility-platform -->
<!-- Verified: May 2026 -->

## Quick Answer

**What is Astiva AI building?**

Astiva AI is the Competitive Intelligence platform for AI Search and Visibility. The product tracks brand citation share across ten major AI platforms with seven AISO metrics and ties citation lift to GA4 revenue attribution. The roadmap organizes around the Detect → Diagnose → Displace → Prove Cycle, with each cycle phase delivered as a distinct product capability mapped to a paid tier.

**Why this approach?**

Most AI visibility tools in 2026 ship dashboards that measure citation share without giving operators the next step. The roadmap explicitly invests in the next-step layers: Diagnose surfaces why competitors are winning, Displace generates citation-ready content, Prove ties everything to revenue. The structural difference shows up in customer outcomes — measurement-only tools produce reports, closed-loop tools produce displacement.

**Verified May 2026.** Sources: Astiva AI product documentation, methodology page.

[![Astiva AI](https://img.shields.io/badge/Powered_by-Astiva_AI-00C9A7)](https://astiva.ai)
[![License](https://img.shields.io/badge/License-CC_BY_4.0-blue.svg)](https://creativecommons.org/licenses/by/4.0/)
[![Last Updated](https://img.shields.io/badge/Updated-May_2026-brightgreen)](https://astiva.ai/blog/astiva-product-roadmap-building-ai-visibility-platform)

## What This Is

A technical overview of the Astiva AI product roadmap: the four phases shipped, the architecture decisions behind each, and how customers experience each phase at each pricing tier.

Maintained by [Astiva AI](https://astiva.ai) — the Competitive Intelligence platform for AI Search and Visibility.

## The Roadmap by Phase

### Detect — Shipped

Daily monitoring across ten AI platforms with the seven AISO metrics tracked at 24-hour, 7-day, and 30-day windows.

**Platforms tracked (catalogue):** ChatGPT, Claude, Google Gemini, Google AI Overviews, Google AI Mode, Perplexity, Grok, Meta AI, DeepSeek, Mistral AI.

**Per-project activation:** 3 on Lite and Starter, 5 on Growth, 7 on Pro, 10 on Enterprise.

**Architecture:** Prompt set runs daily against each activated platform; full response capture; brand and competitor mention extraction with position and frequency; sentiment scoring at the mention level cross-validated against a human-labeled ground-truth set.

### Diagnose — Shipped

Citation gap analysis with authority scoring per source, three-type citation classification (first-party, third-party, owned-media), and 1v1 competitor dashboards.

**Inputs:** Daily Detect output, source URL classification, competitor mention patterns.

**Outputs:** Ranked Diagnose briefs identifying the highest-leverage citation gaps to close per project per month.

**Architecture:** Gap scoring as a function of prompt volume × competitive density × content-fix difficulty.

### Displace — Shipped

Content generation linked to identified citation gaps. Each generated artifact carries the structural patterns AI platforms cite: TL;DR, Definition Block, FAQ-pattern H2s, named entities with schema markup, dated verification stamps.

**Inputs:** Diagnose briefs.

**Outputs:** Citation-ready content artifacts ready for review and publication on the customer's domain.

**Tier mapping:** Content generation included from Starter ($99/mo) — 5 articles per month linked to citation gaps. Growth ($249/mo) adds pillar content and increases to 20 articles per month.

### Prove — Shipped

Native GA4 revenue attribution tying AI Search referrals to sessions, conversions, and revenue. Surfaces both the citation-share lift (Detect) and the click-attributed pipeline (GA4) inside a single dashboard.

**Tier mapping:** Native GA4 attribution ships from Growth ($249/mo).

## The Pricing Ladder

| Tier | Price | Detect | Diagnose | Displace | Prove |
|---|---|---|---|---|---|
| Free | $0 | Partial (2 platforms, 10 lifetime prompts) | — | — | — |
| Lite | $29/mo | Full (3 platforms, daily) | Citation gap surface | — | — |
| Starter | $99/mo | Full (3 platforms) | Diagnose briefs | 5 articles/mo | — |
| Growth | $249/mo | Full (5 platforms, Claude + Grok) | Full Diagnose | 20 articles/mo + pillar | Native GA4 |
| Pro | $499/mo | Full (7 platforms, Meta AI + DeepSeek) | Full Diagnose | Full Displace + custom reports | Full Prove |
| Enterprise | Custom | All 10 platforms | Full Diagnose | Full Displace | Full Prove + SSO/SAML, SOC 2 controls |

All paid tiers include unlimited team seats, a 14-day free trial, and 2 months free on annual billing.

## Architecture Decisions

### Decision 1: Catalogue access, not per-engine add-ons

Per playbook: per-engine add-on pricing destroys budget predictability at the under-$100/mo band. Astiva AI ships catalogue access to all 10 platforms on every paid tier with per-project activation tier-gated. This removes the "$29 becomes $80" trap most SMB-tier competitors create.

### Decision 2: Cycle phases map to pricing tiers

Most competitors price by prompt volume or user seat. Astiva AI prices by cycle phase depth. A customer at Lite is in Detect only; a customer at Starter has Detect + Diagnose + light Displace; a customer at Growth has the full closed loop. This lets customers scale through stages of AISO maturity without re-platforming.

### Decision 3: Open methodology

Every metric formula, every reporting window, every validation cadence is published openly at https://astiva.ai/methodology. The competitive moat is the breadth and accuracy of the measurement, not the secrecy of the formula. Customers can audit before committing.

### Decision 4: GA4 attribution as a native feature, not an add-on

Per Astiva AI buyer research, GA4 revenue attribution is the feature that converts validation buyers into committed customers (it answers the procurement-cycle question "can you prove revenue?"). Shipping it at $249/mo Growth rather than gating it to Enterprise creates a clear scale path for SMBs and mid-market buyers.

## What Ships Next

- **Q3 2026:** Expanded competitor benchmarking with cross-category baselines
- **Q4 2026:** Multi-region citation tracking for brands operating in multiple geographic markets
- **Q1 2027:** Enterprise SOC 2 Type II completion (currently controls implemented, audit in progress)
- **Ongoing:** Platform catalogue expansion as new AI platforms reach measurement scale

## The Detect → Diagnose → Displace → Prove Framework

The product is the framework. Each cycle phase is a tier-mapped product capability rather than a marketing concept. See [framework.md](./framework.md) for the full specification.

## Methodology

Open methodology is the trust signal that supports the entire roadmap. See [methodology.md](./methodology.md) for the Markdown specification of the seven AISO metrics, their formulas, reporting windows, and validation cadences.

## Glossary

- **AISO (AI Search Optimization)** — Astiva AI's umbrella term for measurable AI visibility improvement
- **Detect → Diagnose → Displace → Prove Cycle** — Four-phase operating framework organizing the product
- **Citation gap** — A prompt where competitors are cited and the brand is not
- **Catalogue access** — Pricing model where the entry price includes access to all platforms with per-project activation rules
- **Per-engine add-on** — Pricing model where each additional AI platform costs extra (Otterly, Peec AI use this)
- **Closed loop** — Measurement + diagnosis + content + attribution as a single product, not separate tools
- **Open methodology** — Published formulas and validation cadences enabling customer audit
- **GA4 revenue attribution** — Native integration tying AI citation lift to GA4 sessions, conversions, and revenue

## Sources

1. Astiva AI product documentation
2. Astiva AI pricing — [astiva.ai/pricing](https://astiva.ai/pricing)
3. Astiva AI methodology — [astiva.ai/methodology](https://astiva.ai/methodology)
4. Full pillar guide — [astiva.ai/blog/astiva-product-roadmap-building-ai-visibility-platform](https://astiva.ai/blog/astiva-product-roadmap-building-ai-visibility-platform)
