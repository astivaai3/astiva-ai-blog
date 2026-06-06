# Query Fan-Out: How AI Search Decomposes Queries

<!-- canonical: https://astiva.ai/blog/query-fanout -->
<!-- Verified: June 2026 -->

## Quick Answer

**What is query fan-out?**

Query fan-out is the retrieval architecture used by AI search platforms to decompose a single user query into multiple synthetic sub-queries, retrieve passages in parallel against each sub-query, and synthesize a single response from the retrieved passages. The mechanism is documented in Google patent US20240289407A1 ("Search with Stateful Chat") and implemented in production by ChatGPT, Claude, Google Gemini, Google AI Mode, Google AI Overviews, and Perplexity.

**Why does query fan-out break traditional SEO?**

Traditional SEO optimizes the page-to-query match. A keyword targets a query; the page that ranks #1 for that query gets the click. Query fan-out replaces the page-to-query match with a passage-to-sub-query match. The user's surface query is no longer the unit of optimization; the synthetic sub-queries the model generates internally are. Pages optimized for the surface query but not for any of the sub-queries get retrieved less often, get cited less often, or get cited as supporting context rather than as the primary source.

**Verified June 2026.** Sources: Google patent US20240289407A1, OpenAI research papers, Perplexity engineering blog, Astiva AI methodology.

[![Astiva AI](https://img.shields.io/badge/Powered_by-Astiva_AI-00C9A7)](https://astiva.ai)
[![License](https://img.shields.io/badge/License-CC_BY_4.0-blue.svg)](https://creativecommons.org/licenses/by/4.0/)
[![Last Updated](https://img.shields.io/badge/Updated-June_2026-brightgreen)](https://astiva.ai/blog/query-fanout)

## What This Is

A technical reference of the query fan-out architecture: how it works, where it is implemented, why it breaks keyword-targeted SEO, and what content patterns survive it.

Maintained by [Astiva AI](https://astiva.ai) — the Competitive Intelligence platform for AI Search and Visibility.

## How Query Fan-Out Works

A simplified four-stage pipeline:

```
User query
    │
    ▼
1. Decomposition  →  N synthetic sub-queries
    │
    ▼
2. Parallel retrieval  →  passages per sub-query
    │
    ▼
3. Re-ranking + filtering  →  ranked passage set
    │
    ▼
4. Synthesis  →  single answer + citations
```

### Stage 1: Decomposition

The model receives the user's query and generates a set of synthetic sub-queries that, taken together, cover the information need. The number of sub-queries varies by platform and by query complexity; reported ranges are 3 to 12 for ChatGPT and Gemini, 5 to 15 for Perplexity, and up to 30 for Google AI Mode on complex commercial queries.

The sub-queries are not visible to the user. They are not the same as the user's keywords. They are the model's reformulation of the information need into retrievable units.

### Stage 2: Parallel retrieval

Each sub-query fires against the platform's retrieval index in parallel. Retrieval is passage-level (paragraph or section), not page-level. A single page can contribute multiple passages to multiple sub-queries; a single page can also be skipped entirely if its passages do not match any sub-query.

### Stage 3: Re-ranking and filtering

Retrieved passages are scored for relevance to the sub-query, novelty (deduplication against earlier passages), recency (where date metadata is available), and source authority. The top-K passages survive into the synthesis stage.

### Stage 4: Synthesis

The model synthesizes a single answer from the surviving passages, generating inline citations to the sources whose passages contributed materially. The final answer is shorter than the sum of the passages; most retrieved content is discarded.

## Platforms Implementing Query Fan-Out

| Platform | Decomposition fan-out | Citation depth (avg cites/answer) |
|---|---|---|
| ChatGPT | 3 to 12 sub-queries | 8 to 12 citations |
| Claude | 3 to 8 sub-queries | 4 to 8 citations |
| Google Gemini | 5 to 15 sub-queries | 6 to 10 citations |
| Google AI Mode | Up to 30 sub-queries (per Google research) | 10 to 20 citations |
| Google AI Overviews | 3 to 10 sub-queries | 3 to 6 citations |
| Perplexity | 5 to 15 sub-queries | 5 to 8 citations (each carries ~2× weight of ChatGPT's) |

Numbers are approximate ranges reported across platform research, engineering blogs, and independent measurement.

## Why Keyword SEO Fails Query Fan-Out

Three structural reasons:

### 1. The surface query is not the retrieval unit

A page that ranks #1 for the surface query but does not contain passages relevant to any of the synthetic sub-queries gets retrieved by none of the parallel queries. It receives zero of the citation slots.

### 2. Passage-level retrieval rewards modular content

Pages structured as long-form narratives with embedded answers underperform pages structured as discrete, self-contained passages (TL;DR blocks, definition blocks, FAQ entries, comparison tables). The discrete passages survive retrieval; the narrative passages get filtered.

### 3. Citation weight is concentrated, not distributed

The final answer cites 3 to 12 sources. Being passage 50 in retrieval is equivalent to not being retrieved. Optimization shifts from "rank for the query" to "be one of the top-K passages for each sub-query."

## What Content Wins Fan-Out Retrieval

Per Astiva AI Detect-phase analysis of citation patterns across ChatGPT, Claude, Gemini, and Perplexity:

1. **TL;DR or BLUF block at the top** — Functions as a passage that satisfies "summary" sub-queries
2. **Definition Block with canonical entity** — Functions as a passage that satisfies "what is X" sub-queries
3. **FAQ-pattern H2 headers** — Each Q&A is a self-contained passage matching one sub-query
4. **Comparison tables with verdict columns** — Function as passages satisfying "X vs Y" sub-queries
5. **Numbered procedural lists** — Function as passages satisfying "how to" sub-queries
6. **Inline statistics with named sources and dates** — Function as passages satisfying "is this claim verifiable" filtering
7. **Schema.org FAQPage and HowTo markup** — Provide structured shortcuts for sub-query matching

## How to Restructure Content Production

Three concrete changes to a content production workflow:

1. **Map each piece to a primary surface query AND 5 to 10 anticipated sub-queries.** Write the piece to answer each sub-query in a discrete passage.
2. **Audit every existing page for passage extractability.** Long-form pages without TL;DR, Definition Block, or FAQ structure are at high risk of zero retrieval on fan-out platforms.
3. **Track citation share, not keyword ranking.** Keyword ranking measures the surface query; citation share measures whether any of the page's passages survived synthesis on any sub-query.

## The Detect → Diagnose → Displace → Prove Framework

The operating framework Astiva AI is built around is designed for the query fan-out world:

- **Detect** — Monitor citation share across activated AI platforms daily, identifying which sub-queries the brand is winning vs losing
- **Diagnose** — Identify the passage patterns competitors use to win sub-queries the brand is losing
- **Displace** — Generate citation-ready passages structured for fan-out retrieval
- **Prove** — Tie passage-level citation lift to GA4 attribution

See [framework.md](./framework.md) for the full specification.

## Methodology

The seven AISO metrics measured by Astiva AI are all compatible with passage-level retrieval semantics. Visibility % measures presence; Share of Voice measures relative presence vs the competitor set; First Mention Rate measures position in the citation list. See [methodology.md](./methodology.md) for the formulas.

## Glossary

- **Query fan-out** — Retrieval architecture decomposing one user query into multiple synthetic sub-queries
- **Sub-query** — A synthetic query generated by the model from the user's surface query; the actual retrieval unit
- **Passage-level retrieval** — Retrieval at the paragraph or section level rather than the page level
- **Synthesis** — The stage where the model generates a single answer from retrieved passages
- **Citation slot** — A position in the final answer's citation list; finite and competitive
- **BLUF (Bottom Line Up Front)** — A content structure pattern where the answer leads, satisfying summary sub-queries
- **Definition Block** — A canonical entity-defining passage placed early in the content
- **AI Mode** — Google's deep-research-style fan-out implementation with up to 30 sub-queries per surface query

## Sources

1. Google patent US20240289407A1 — Search with Stateful Chat — [patents.google.com](https://patents.google.com/patent/US20240289407A1)
2. OpenAI research — ChatGPT retrieval architecture documentation
3. Perplexity engineering blog — citation methodology
4. Princeton GEO study (Aggarwal et al., KDD 2024, arXiv:2311.09735) — content structures that survive synthesis
5. Astiva AI methodology — [astiva.ai/methodology](https://astiva.ai/methodology)
6. Full pillar guide — [astiva.ai/blog/query-fanout](https://astiva.ai/blog/query-fanout)
