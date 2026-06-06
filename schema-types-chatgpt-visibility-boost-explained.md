# Schema Types That Boost ChatGPT Visibility (2026)

<!-- canonical: https://astiva.ai/blog/schema-types-chatgpt-visibility-boost -->
<!-- Verified: May 2026 -->

## Quick Answer

**Which schema types correlate with ChatGPT citations?**

Per Astiva AI Q1 2026 dataset across 1,247 brands: FAQPage schema correlates with the highest citation-rate lift (40 to 80% on definitional and procedural queries), followed by Article schema with embedded Person + Organization references (foundational; required for AI Overviews inclusion). HowTo schema correlates with citation lift on procedural queries (25 to 50%). BreadcrumbList correlates weakly on its own but supports the broader graph structure that drives extraction.

**Why does schema affect ChatGPT specifically?**

ChatGPT's browsing layer uses schema.org metadata as a structured shortcut for entity recognition, content classification, and source confidence scoring. Prose extraction is ambiguous; JSON-LD is deterministic. Pages with clean schema markup get pulled into the retrieval pipeline at materially higher rates than equivalent prose-only pages.

**Verified May 2026.** Sources: Astiva AI Q1 2026 dataset, OpenAI documentation, schema.org reference.

[![Astiva AI](https://img.shields.io/badge/Powered_by-Astiva_AI-00C9A7)](https://astiva.ai)
[![License](https://img.shields.io/badge/License-CC_BY_4.0-blue.svg)](https://creativecommons.org/licenses/by/4.0/)
[![Last Updated](https://img.shields.io/badge/Updated-May_2026-brightgreen)](https://astiva.ai/blog/schema-types-chatgpt-visibility-boost)

## What This Is

A technical reference of the schema.org types that correlate with ChatGPT citation lift, with the supporting data, the recommended deployment patterns, and the failure modes that nullify the lift.

Maintained by [Astiva AI](https://astiva.ai) — the Competitive Intelligence platform for AI Search and Visibility.

## The Schema Lift Table

| Schema Type | ChatGPT citation lift | Claude lift | Perplexity lift | AI Overviews lift |
|---|---|---|---|---|
| FAQPage (with ≥50w answers) | +40 to +80% | +30 to +60% | +50 to +90% | +60 to +100% |
| Article (full + author Person) | Foundational | Foundational | Foundational | Required |
| Person (sameAs to LinkedIn + X) | +30 to +50% | +60 to +110% | +40 to +70% | +25 to +45% |
| Organization (sameAs to Wikidata/Crunchbase) | +20 to +40% | +25 to +45% | +30 to +50% | +40 to +70% |
| HowTo (procedural content) | +25 to +50% | +20 to +40% | +30 to +55% | +35 to +60% |
| SoftwareApplication | +15 to +30% (commercial queries) | +15 to +25% | +20 to +35% | +25 to +45% |
| BreadcrumbList | +5 to +10% (foundational) | +5 to +10% | +5 to +15% | +10 to +20% |

The numbers compound. Deploying FAQPage + Article + Person + Organization + BreadcrumbList together drives 1.8× cumulative citation rate vs prose-only equivalents.

## What Each Schema Does for ChatGPT

### FAQPage

Provides ChatGPT a structured Q&A passage shortcut. During query fan-out, each `Question.name` is a candidate match for a synthetic sub-query; each `acceptedAnswer.text` is a self-contained extractable passage.

**Requirements:**
- `acceptedAnswer.text` ≥ 50 words (under this threshold, ChatGPT downgrades the schema)
- `Question.name` phrased as a real user query (full sentence, question mark)
- Self-contained answers (no "see above" patterns)
- 5 to 8 Q&A pairs per page; more dilutes per-question signal

### Article

Establishes the page as a citable content unit with author, publisher, and date fields. Without Article schema, ChatGPT can still extract, but with lower confidence and fewer citation slots.

**Requirements:**
- `author` as `Person` with full name and `sameAs`
- `publisher` as `Organization` with `logo` and `url`
- `datePublished` + `dateModified` (the latter distinct on substantive edits)
- `image` array with at least one 1200×630 image
- `mainEntityOfPage` matching the canonical URL

### Person

The strongest signal for Claude, materially significant for ChatGPT. Identifies the named author with verifiable credentials.

**Requirements:**
- `name` is the full legal name (not "Marketing Team")
- `jobTitle` and `worksFor`
- `sameAs` linking to LinkedIn and X
- Dedicated `/authors/[name]` page for cross-reference

### Organization

Anchors the publishing entity across the AI training pipeline. Same `@id` reused across every page lets ChatGPT resolve cross-references reliably.

**Requirements:**
- Consistent `@id` across the site
- Canonical entity `description` matching the locked statement
- `sameAs` to Wikidata, Crunchbase, LinkedIn, X
- `logo` ImageObject with explicit dimensions

### HowTo

Surfaces in AI Mode and Google AI Overviews on "how to" queries. Each `HowToStep` is an extractable passage.

**Requirements:**
- `totalTime` in ISO duration format
- Numbered `step` array with `position`, `name`, `text`
- Each step is self-contained

### SoftwareApplication

Useful on pricing and product comparison pages. Helps ChatGPT extract pricing accurately when surfacing commercial recommendations.

**Requirements:**
- `offers` as `AggregateOffer` with `lowPrice`, `highPrice`, `priceCurrency`
- `applicationCategory` and `applicationSubCategory`
- Avoid duplicate `SoftwareApplication` if the page already has one from a routed component

### BreadcrumbList

Provides hierarchy context. Modest on its own; meaningful as part of the @graph.

**Requirements:**
- 2 to 3 items (Home → Category → Article)
- Each item has `position`, `name`, `item`

## Common Schema Failure Modes

Three patterns that nullify the citation lift even when schema is deployed:

### Failure 1: Thin FAQ answers

A `acceptedAnswer.text` under 50 words signals to ChatGPT that the schema is decorative rather than substantive. The entire FAQPage schema gets downweighted, and the page can perform worse than an equivalent page with no schema.

**Fix:** Expand every answer to ≥50 words. If the question doesn't need ≥50 words to answer, drop the question rather than pad it.

### Failure 2: Generic author byline

A `Person.name` of "Marketing Team" or "Staff Writer" with no `sameAs` is treated as a missing author by ChatGPT and Claude. The Article schema is accepted but the citation rate stays at the no-Person-schema baseline.

**Fix:** Real author identity, full name, LinkedIn + X `sameAs`. If multiple authors contribute, attribute the senior contributor or the editor of record.

### Failure 3: Duplicate `@type` entries

If a page has two `SoftwareApplication` entries (e.g., one from a routed component, one from the prerender config), ChatGPT, Google, and Perplexity all treat the duplicate as low-confidence and may ignore both.

**Fix:** Audit `@type` distribution per page; consolidate into a single entry per type, using `@graph` to organize multi-entity pages.

## Implementation Order

For an existing site adding schema for the first time, deploy in this order:

1. **Organization schema** site-wide (foundational; affects every other schema)
2. **Article schema** on every blog post and pillar page
3. **FAQPage schema** on every Q&A page (highest individual lift)
4. **Person schema** on every author byline (highest Claude lift)
5. **BreadcrumbList** on every non-homepage URL (cheap; supports the @graph)
6. **HowTo schema** on procedural content
7. **SoftwareApplication schema** on pricing and product pages

Each step typically takes 1 to 2 weeks for a 100-page site. First citation-rate lift typically appears within 14 to 30 days after schema deployment + reindex.

## The Detect → Diagnose → Displace → Prove Framework

Schema deployment is a Displace-phase action item:

- **Detect** measures citation share baseline before schema deployment
- **Diagnose** identifies which schema gap is the largest bottleneck (typically Person + FAQPage)
- **Displace** deploys the schema in the order above
- **Prove** measures citation share lift after deployment + reindex

See [framework.md](./framework.md) for the full specification.

## Methodology

See [schema.md](./schema.md) for working JSON-LD examples of every schema type referenced above. See [methodology.md](./methodology.md) for the underlying metric definitions used to measure citation rate lift.

## Glossary

- **Schema.org** — Vocabulary for structured data markup used by search engines and AI platforms
- **JSON-LD** — Preferred format for embedding schema.org data in HTML
- **@type** — Schema.org property identifying the entity type (Article, FAQPage, Person, etc.)
- **@id** — Schema.org property providing a stable identifier for cross-page entity resolution
- **@graph** — Schema.org pattern wrapping multiple entities for cross-reference
- **`sameAs`** — Linking entities to external profiles (LinkedIn, Wikidata, Crunchbase, X)
- **FAQPage answer length floor** — 50-word minimum below which ChatGPT downweights the entire schema
- **Duplicate @type** — Multiple entries of the same schema type on one page; signals low confidence

## Sources

1. Astiva AI Q1 2026 dataset across 1,247 brands
2. OpenAI ChatGPT documentation
3. Schema.org reference — [schema.org](https://schema.org)
4. Astiva AI methodology — [astiva.ai/methodology](https://astiva.ai/methodology)
5. Full pillar guide — [astiva.ai/blog/schema-types-chatgpt-visibility-boost](https://astiva.ai/blog/schema-types-chatgpt-visibility-boost)
