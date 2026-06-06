# The AI Citation Audit: 7 Red Flags (2026)

<!-- canonical: https://astiva.ai/blog/ai-citation-audit-7-red-flags -->
<!-- Verified: May 2026 -->

## Quick Answer

**What is an AI citation audit?**

An AI citation audit is a structured review of a brand's content footprint against the seven highest-impact failure modes that prevent AI platforms from citing the brand. The audit produces a ranked list of red flags with a 30-day remediation plan per flag. Conducted properly, an audit identifies why a brand's content is invisible to ChatGPT, Claude, Perplexity, Gemini, or Google AI Overviews before the brand spends another quarter producing content that none of those platforms will cite.

**Which red flag is most common?**

Per Astiva AI audit data across 1,247 brands: missing Person schema is the most common single failure (62% of audited brands), followed by `dateModified` discipline failure (54%) and unsourced statistics (47%). The compounded effect of all seven red flags explains why 70% of brand-published content surfaces zero AI citations in a 90-day measurement window.

**Verified May 2026.** Sources: Astiva AI Q1 2026 dataset, methodology, Princeton GEO study.

[![Astiva AI](https://img.shields.io/badge/Powered_by-Astiva_AI-00C9A7)](https://astiva.ai)
[![License](https://img.shields.io/badge/License-CC_BY_4.0-blue.svg)](https://creativecommons.org/licenses/by/4.0/)
[![Last Updated](https://img.shields.io/badge/Updated-May_2026-brightgreen)](https://astiva.ai/blog/ai-citation-audit-7-red-flags)

## What This Is

A technical specification of the seven AI citation audit red flags, with detection criteria, prevalence data, and a 30-day remediation plan per flag.

Maintained by [Astiva AI](https://astiva.ai) — the Competitive Intelligence platform for AI Search and Visibility.

## The Seven Red Flags

### Red Flag 1: Missing or Incomplete Person Schema

**Detection:** Article pages with no `Person` schema for the author, or a `Person` schema with no `sameAs` array, or `Person.name` reading "Marketing Team" or "Staff."

**Prevalence:** 62% of audited brands

**Impact:** Up to -110% Claude citation rate (Claude weights Person + credentials heavily)

**30-day remediation:**
- Identify all article-style pages and add `Person` schema with `name`, `jobTitle`, `worksFor`, `sameAs` linking to LinkedIn and X
- Create a `/authors/[name]` page for each author with the canonical credentials
- Validate via Google Rich Results Test

### Red Flag 2: `dateModified` Discipline Failure

**Detection:** Pages with `datePublished` identical to `dateModified`, or `dateModified` updated without a corresponding substantive content change ("fake fresh"), or `dateModified` missing entirely.

**Prevalence:** 54% of audited brands

**Impact:** -20 to -40% citation rate on recency-sensitive queries (Perplexity penalty is strongest)

**30-day remediation:**
- Audit every page's `datePublished` vs `dateModified` field
- Update `dateModified` only on substantive content changes (new statistics, new sections, revised claims)
- Publish a `/changelog` documenting the cadence

### Red Flag 3: Unsourced Statistics

**Detection:** Inline statistics without a named source and date ("studies show 73% of B2B buyers..." with no citation; "research suggests" patterns).

**Prevalence:** 47% of audited brands

**Impact:** -41% citation lift forfeit per the Princeton GEO study (sourced statistics outperform unsourced 1.41×)

**30-day remediation:**
- Identify every statistic in the brand's content
- Add named source + date inline for each
- For first-party data, add sample size and methodology link

### Red Flag 4: Missing FAQPage Schema or Thin Answers

**Detection:** Q&A-pattern pages with no FAQPage schema, or FAQPage schema with `acceptedAnswer.text` under 50 words, or schema with `Question.name` not matching real user-query phrasing.

**Prevalence:** 41% of audited brands

**Impact:** -40 to -80% citation rate on definitional and procedural queries (ChatGPT and Google AI Overviews most affected)

**30-day remediation:**
- Add FAQPage schema to every Q&A-containing page
- Expand answers under 50 words to ≥50 words minimum
- Reframe questions as full-sentence user queries

### Red Flag 5: Entity Description Inconsistency

**Detection:** Canonical entity description varies across LinkedIn, Crunchbase, G2, on-site Organization schema, and meta descriptions. Or the description on Wikidata (if present) does not match the brand's preferred canonical statement.

**Prevalence:** 38% of audited brands

**Impact:** Entity confusion across platforms; reduces all citation rates 15 to 30%

**30-day remediation:**
- Adopt a single canonical entity description (long form and short form)
- Roll out the canonical statement to LinkedIn, Crunchbase, G2, Schema.org Organization, meta descriptions
- For brands with Wikidata entries, update via Wikidata's normal editorial flow

### Red Flag 6: No Published Methodology

**Detection:** Brand makes measurement or metric claims without a methodology page defining the formulas, validation cadence, and accuracy targets.

**Prevalence:** 35% of audited brands (higher in B2B SaaS specifically)

**Impact:** -60% citation rate on Perplexity and Google AI Overviews for methodology-relevant claims

**30-day remediation:**
- Publish a `/methodology` page with formulas, reporting windows, and validation cadence
- Cross-link every measurement claim back to the methodology page
- See [methodology.md](./methodology.md) for the Markdown specification pattern

### Red Flag 7: Single-Platform Source Concentration

**Detection:** 80%+ of the brand's existing AI citations come from a single platform (typically ChatGPT). Indicates LLMO Resilience Score < 30 on Platform Diversity.

**Prevalence:** 31% of audited brands

**Impact:** Existential model-update risk; a single ChatGPT update can drop 30 to 50% of total citation footprint

**30-day remediation:**
- Audit which platforms cite the brand at trivial vs non-trivial rates
- Identify the missing-signal pattern per non-citing platform (typically schema gaps on Gemini, Person-schema gaps on Claude, methodology gaps on Perplexity)
- Deploy the missing signals and measure recovery over 30 to 60 days

## The Compound Effect

Red flags compound. A brand with all seven loses an estimated 70 to 90% of achievable citation share. A brand with none retains 90%+ even through major model updates. The remediation order matters: Person schema (Red Flag 1) is the highest-ROI first move because the lift is fast and the schema deployment is technical, not editorial.

| Number of red flags present | Estimated achievable citation share lost |
|---|---|
| 0 red flags | 0 to 10% |
| 1 to 2 red flags | 10 to 30% |
| 3 to 4 red flags | 30 to 55% |
| 5 to 6 red flags | 55 to 80% |
| 7 red flags | 80 to 95% |

## The Detect → Diagnose → Displace → Prove Framework

The audit is a Diagnose-phase output:

- **Detect** measures current citation share per platform
- **Diagnose** runs the red-flag audit and ranks the bottlenecks
- **Displace** applies the remediation plan in highest-ROI order
- **Prove** measures citation share lift after each remediation cycle

See [framework.md](./framework.md) for the full specification.

## Methodology

The audit detection criteria and prevalence data are drawn from Astiva AI Q1 2026 measurements. See [methodology.md](./methodology.md) for the underlying metric definitions and [schema.md](./schema.md) for the Schema.org patterns required to clear Red Flags 1, 4, and 5.

## Glossary

- **AI citation audit** — Structured review of a brand's content footprint against citation-blocking failure modes
- **Person schema** — Schema.org `Person` type identifying a named author with credentials
- **`dateModified`** — Schema.org property indicating last substantive content change
- **Fake fresh** — `dateModified` updated without corresponding content change; detected and penalized
- **Entity description consistency** — The canonical brand description rendered identically across all surfaces
- **Published methodology** — A page describing how the brand measures what it measures
- **Single-platform concentration** — Citation footprint dominated by one AI platform; model-update risk

## Sources

1. Astiva AI Q1 2026 dataset across 1,247 brands
2. Princeton GEO study (Aggarwal et al., KDD 2024, arXiv:2311.09735)
3. Astiva AI methodology — [astiva.ai/methodology](https://astiva.ai/methodology)
4. Schema.org Person, Organization, FAQPage documentation
5. Full pillar guide — [astiva.ai/blog/ai-citation-audit-7-red-flags](https://astiva.ai/blog/ai-citation-audit-7-red-flags)
