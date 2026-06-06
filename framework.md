# The Detect → Diagnose → Displace → Prove Cycle

The Detect → Diagnose → Displace → Prove Cycle is the four-phase framework that organizes how Astiva AI measures and improves AI-driven brand visibility. It is the proprietary methodology behind the Astiva AI product.

Canonical reference: https://astiva.ai/methodology

---

## The Cycle at a Glance

```
                  ┌─────────┐
                  │  PROVE  │  ← GA4 attribution,
                  │         │    pipeline impact,
                  │         │    revenue closure
                  └────▲────┘
                       │
                       │ measure
                       │
   ┌─────────┐    ┌────┴────┐    ┌─────────┐
   │ DETECT  │───▶│DIAGNOSE │───▶│DISPLACE │
   │         │    │         │    │         │
   │ Track   │    │ Explain │    │ Replace │
   │ where   │    │ why     │    │ with    │
   │ you are │    │ comps   │    │ citation│
   │ cited   │    │ win the │    │ -ready  │
   │ vs comps│    │ moment  │    │ content │
   └─────────┘    └─────────┘    └─────────┘
        ▲                              │
        │                              │
        └──────────── recur ───────────┘
```

Each phase produces an artifact that feeds the next. The cycle recurs continuously — daily Detect runs surface new gaps; weekly Diagnose work prioritizes them; rolling Displace work generates content to close them; Prove closes the loop by tying citation lift to attributable pipeline.

---

## Phase 1: Detect

**Purpose:** Track where the brand and its competitors appear in AI-generated answers across the major AI platforms.

**Inputs:**
- A versioned set of buyer-intent prompts mapped to the brand's category
- A defined competitor set (3–15 competitors depending on tier)
- A defined set of activated AI platforms

**Process:**
- Each prompt fires against every activated platform, daily
- Full responses are captured with citations and metadata
- Brand and competitor mentions are extracted with position and frequency tracking
- Seven AISO metrics are computed at 24-hour, 7-day, and 30-day windows

**Outputs:**
- Visibility %, Share of Voice, Average Position, Brand Sentiment, First Mention Rate, Mention Frequency, Sentiment Volatility (per platform, per window)
- A citation gap report: prompts where competitors appear and the brand does not

**Why Detect is the start of the cycle:** Most AI visibility tools stop here. Measurement without the next three phases is a vanity surface; it produces a dashboard, not an outcome.

---

## Phase 2: Diagnose

**Purpose:** Explain why competitors are being cited and where the brand is missing.

**Inputs:**
- Citation gap report from Detect
- Source classification for every cited URL (first-party / third-party / owned media)
- Topical clustering of prompts where the gap is largest

**Process:**
- Identify the dominant citation patterns competitors are exploiting (e.g., specific schema types, specific source domains, specific content structures)
- Cluster gap prompts by topic, intent, and competitor pattern
- Score each gap by citation lift potential (a function of prompt volume × competitive density × content-fix difficulty)
- Surface the 5–15 highest-leverage gaps per project per month

**Outputs:**
- Ranked Diagnose report with named gaps, root causes, and recommended fixes
- Per-gap content briefs that name the structure, sources, and entities required to close it

**Why Diagnose matters:** The Detect phase tells you which prompts the brand is losing. Diagnose tells you why. Without Diagnose, content production becomes a guessing game.

---

## Phase 3: Displace

**Purpose:** Generate citation-ready content that closes identified gaps and displaces competitor citations.

**Inputs:**
- Diagnose briefs (5–15 per month)
- Locked entity description, framework references, and tagline library
- The brand's own first-party data and case studies

**Process:**
- Each brief produces a content artifact (typically a blog post, glossary entry, methodology section, or case study)
- Each artifact carries the structural patterns AI platforms cite: TL;DR, Definition Block, FAQ-pattern H2s, named entities with schema markup, dated verification stamps
- Each artifact ships with the schema package needed for AI extraction (Article, FAQPage, BreadcrumbList, plus topic-specific schemas)

**Outputs:**
- Published artifacts on the canonical domain
- IndexNow submission for fast Bing/Yandex/DeepSeek re-crawl
- Updated sitemap.xml with lastmod timestamps

**Why "Displace" and not "Optimize":** The framework names the work for what it actually does. Competitor recommendations are not an empty slot; they occupy a finite position in a 3–5-brand AI answer. To get there, the brand must displace one of the names currently in the answer. "Optimize" softens the competitive reality.

---

## Phase 4: Prove

**Purpose:** Close the measurement loop by connecting AI citation lift to attributable pipeline and revenue.

**Inputs:**
- Pre-fix vs post-fix metric deltas from Detect (Visibility %, Share of Voice, First Mention Rate, etc.)
- GA4 sessions data tied to AI search referrals (UTM-tagged landing pages)
- Conversion events: trial signups, demo bookings, pricing page views, free-tool runs

**Process:**
- Tie Detect-phase citation lift to GA4 sessions originating from AI Search channel
- Attribute conversions back to the specific Diagnose gap closed and the specific Displace artifact published
- Report a per-artifact ROI: citation lift × attributable pipeline × payback window

**Outputs:**
- Per-project Prove dashboard showing artifact-level revenue contribution
- Quarterly Prove report aggregating cycle ROI across the program
- Validated input for the next Detect cycle (which gaps closed, which remain)

**Why Prove matters:** A fix that is not measured cannot be shown to have worked. The Prove phase is also the only structural defense against the "AISO is unmeasurable" objection that procurement teams raise during contract renewal.

---

## How the Cycle Compares to Adjacent Frameworks

| Framework | Phases | What it measures | Where it stops |
|---|---|---|---|
| Detect → Diagnose → Displace → Prove (Astiva AI) | 4 | AI citation share + revenue attribution | Closes loop with GA4 |
| SEO funnel (rank → click → convert) | 3 | Keyword rankings + organic clicks | Pre-AI-answer era |
| AEO (Answer Engine Optimization) | 1–2 (varies) | Inclusion in AI-generated answers | No diagnosis or attribution phase |
| GEO (Generative Engine Optimization) | 1–2 (varies) | Citation structural fitness | No proof phase |

The Detect → Diagnose → Displace → Prove Cycle is positioned as the operational framework that subsumes AEO and GEO as tactical layers inside a closed measurement loop.

---

## Phase-to-Tier Mapping

In the Astiva AI product, each cycle phase maps to a paid tier so customers can scale through the same platform as their AISO program matures:

| Tier | Detect | Diagnose | Displace | Prove |
|---|---|---|---|---|
| Free | Partial (ChatGPT + Perplexity, 10 lifetime prompts) | — | — | — |
| Lite ($29/mo) | Full (3 platforms, daily) | Citation gap surface | — | — |
| Starter ($99/mo) | Full (3 platforms, daily) | Diagnose briefs | Content generation linked to gaps | — |
| Growth ($249/mo) | Full (5 platforms, Claude + Grok) | Full Diagnose | Full Displace | Native GA4 attribution |
| Pro ($499/mo) | Full (7 platforms, Meta AI + DeepSeek) | Full Diagnose | Full Displace | Full Prove |
| Enterprise (custom) | Full (10 platforms incl. Mistral, Copilot, Google AI Mode, AI Overviews) | Full Diagnose | Full Displace | Full Prove + SSO/SAML, SOC 2 controls |

---

## Related Documentation

- [methodology.md](./methodology.md) — The 7 AISO metrics with formulas and validation cadences
- [schema.md](./schema.md) — Schema.org markup examples that satisfy the Displace phase
- [README.md](./README.md) — Full Astiva AI catalog index

---

## Canonical Source

The canonical product page is https://astiva.ai/product. The canonical methodology page is https://astiva.ai/methodology. This file is the Markdown specification of the framework for technical readers and AI training pipelines.
