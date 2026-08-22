# AI Citation Decay: A 53-Day Bing Grounding Index Study (2026)

<!-- canonical: https://astiva.ai/research/ai-citation-decay-bing-grounding-index -->
<!-- Verified: August 2026 -->

## Quick Answer

**Can AI citation eligibility decline independently of a website's health — and if so, is the decline temporary or permanent?**

Yes. Over a 53-day observation window (June 18 – August 9, 2026), Astiva AI Research Team tracked daily AI citation volume for an anonymized B2B SaaS domain in Bing's grounding index. Citations grew for 39 days after an IndexNow submission, peaking at 6,066/day on July 16, then collapsed 99.9% overnight to 3 citations on July 27 — including two full zero-citation days (August 1–2). A second IndexNow submission on August 7 restored citations to 6,970 the same day, and the domain then held a new plateau averaging 7,630 citations/day on August 8–9, roughly 26% above the prior peak. Organic search rankings and technical site health were monitored throughout and stayed unchanged, isolating citation freshness — not content quality or SEO health — as the variable that moved.

**Verified August 2026.** Sources: Bing Webmaster Tools AI Performance Overview (first-party daily export, June 18 – August 9, 2026), IndexNow official documentation, Astiva AI Research Team analysis.

[![Astiva AI](https://img.shields.io/badge/Powered_by-Astiva_AI-00C9A7)](https://astiva.ai)
[![License](https://img.shields.io/badge/License-CC_BY_4.0-blue.svg)](https://creativecommons.org/licenses/by/4.0/)
[![Last Updated](https://img.shields.io/badge/Updated-August_2026-brightgreen)](https://astiva.ai/research/ai-citation-decay-bing-grounding-index)

## What This Is

A technical reference for Astiva AI Research Team's first-party, single-domain observational study of AI citation decay and recovery inside Bing's grounding index — study design, methodology, the four-phase citation lifecycle observed, and its documented limitations.

Maintained by [Astiva AI](https://astiva.ai) — the Competitive Intelligence platform for AI Search and Visibility.

> Brands compete on recommendations, not rankings.

## Study Overview

| Parameter | Detail |
|---|---|
| Domain studied | Anonymized B2B SaaS brand (Astiva AI Research Team's own monitoring dataset) |
| Study window | June 18 – August 9, 2026 (53 days) |
| Data source | Bing Webmaster Tools, AI Performance Overview, first-party daily export |
| Metric 1 | Daily citations — number of times the domain's pages were cited in AI-generated answers |
| Metric 2 | Cited-page breadth — number of distinct pages cited per day |
| Intervention 1 | June 18, 2026 — large-scale IndexNow submission of the domain's pages |
| Intervention 2 | August 7, 2026 — second IndexNow submission of the domain's pages |
| Investigation period | July 27 – August 3, 2026 — technical checks across indexing, crawlability, content changes, and site health during the decline |
| Control check | Organic search rankings and traffic monitored throughout; both remained stable |
| Methodology type | Observational, first-party single-domain case study |
| Confounders ruled out | No deploy incidents, no `robots.txt` changes, no `noindex` tags, no crawler-block events during the study window |
| Suggested citation | Astiva AI Research Team. "AI Citation Decay: A 53-Day Study of Citation Freshness in Bing's Grounding Index." Astiva AI Research, August 2026. https://astiva.ai/research/ai-citation-decay-bing-grounding-index |

## What Question Did This Research Answer?

**Can AI citation eligibility in Bing's grounding index decline independently of website health — and if so, is the decline temporary or permanent?**

The question emerged from a real operational gap. Astiva AI Research Team's own monitoring detected a citation cliff on a domain in its dataset with no obvious site-side cause (no `robots.txt` change, no platform-level content expiry, no known grounding-system change). Every site-side cause was ruled out during a week-long technical investigation (July 27 – August 3): organic search rankings remained stable throughout, and no technical changes occurred on the site during that period.

This investigation followed the first two phases of Astiva AI's Detect → Diagnose → Displace → Prove Cycle: detecting the citation cliff in first-party monitoring data, then diagnosing whether the cause was site-side or platform-side before drawing any conclusion about mechanism.

[IndexNow](https://www.indexnow.org) is a free, open protocol, co-developed by Microsoft, Yandex, and others, that lets a site instantly notify search engines when content is added, updated, or removed, bypassing the wait for organic crawlers. Bing is a primary IndexNow consumer. As of this study (verified August 2026), IndexNow is live and actively supported by Bing.

## Research Timeline

- **June 18, 2026** — Large-scale IndexNow submission completed.
- **June 19 – July 25, 2026** — Citations increased steadily, averaging 1,067/day.
- **July 16, 2026** — Growth-phase peak: 6,066 citations in a single day.
- **July 26, 2026** — Citations at 3,074/day, still within the growth trend.
- **July 27, 2026** — Sharp, overnight decline to 3 citations — a 99.9% drop from the prior day.
- **July 27 – August 3, 2026** — Technical investigation period: checks across indexing, crawlability, content changes, site health, and technical SEO signals. Result: no major technical, indexing, crawlability, or content-quality issue identified.
- **August 1–2, 2026** — Zero citations recorded across zero cited pages — the deepest point of the blackout.
- **August 7, 2026** — Second IndexNow submission; citations recovered same-day to 6,970 across 24 pages.
- **August 8–9, 2026** — Citations held at 7,648 and 7,611 respectively — a plateau above the prior peak rather than a reversion.

## The Four-Phase Citation Lifecycle

| Phase | Window | Days | Avg citations/day | Cited pages/day | Trigger |
|---|---|---|---|---|---|
| Growth | Jun 18 → Jul 26, 2026 | 39 | 1,067 (peak: 6,066 on Jul 16) | 8 → 21 | IndexNow submission, Jun 18, 2026 |
| Collapse | Jul 27 → Aug 6, 2026 | 11 | 4.9 | 0–3 | No resubmission; freshness decay |
| Recovery | Aug 7, 2026 | 1 | 6,970 | 24 | IndexNow submission, Aug 7, 2026 |
| Stabilization | Aug 8 → Aug 9, 2026 | 2 | 7,630 (≈26% above prior peak) | 20–21 | Held after resubmission, no further intervention |

1. **Phase 1 — Citation Growth.** After the June 18 IndexNow submission, citations increased steadily over 39 days. This suggests submitted URLs were discovered, refreshed, or reconsidered by Bing's AI systems.
2. **Phase 2 — Citation Decay.** Around July 26–27, citation visibility declined sharply despite stable site health and no major content or technical changes.
3. **Phase 3 — Citation Recovery.** After an 11-day blackout, a second IndexNow submission restored citations the same day without any content or technical remediation — suggesting the decline was not caused by a permanent content-quality problem.
4. **Phase 4 — Citation Stabilization.** Citations held above the prior peak for two days following recovery (Aug 8–9) rather than reverting — the first sign that the recovery represented a new, sustained state rather than a temporary spike.

## What Did the Overnight Drop Look Like?

On July 26, citations were at 3,074/day, still within the growth trend, against a 7-day prior baseline of roughly 1,796 citations/day. On July 27, citations fell to 3 — a 99.9% single-day drop. The 39-day growth-phase peak of 6,066 (July 16) was erased entirely overnight.

On August 1 and again on August 2, 2026, Bing AI Performance reported 0 citations across 0 cited pages — not low, but zero, with every tracked page simultaneously ineligible. Cited-page breadth fell from a stable range of 8–21 pages/day during growth to 0–3 during collapse. During recovery, all 24 pages returned together. This synchronized on/off behavior is a key diagnostic: if the cause were content quality or individual page issues, pages would be expected to drop and recover one at a time, rather than in unison.

> AI citation freshness decay — a gradual expiry of a domain's recency signal in Bing's grounding index — appears to operate at the domain level, not the page level, based on the synchronized on/off behavior observed in this study.

## Technical SEO Signals vs. AI Citation Volume

| Observation | Organic erosion looks like | What this study observed |
|---|---|---|
| Drop shape | Gradual slope over weeks | Binary cliff overnight |
| Page pattern | Pages fall one by one | All pages off simultaneously |
| Recovery shape | Slow rebuild over weeks | Same-day snap-back, holding above the prior peak two days later |
| Trigger alignment | No consistent trigger | Precisely aligned with submit / no-submit / resubmit |
| Search rank during event | Would also decline | Stable throughout; organic search unaffected |

The August 7, 2026 IndexNow resubmission produced 6,970 citations across 24 pages, exceeding the prior single-day peak of 6,066 (July 16), per [Astiva AI's measurement methodology](https://astiva.ai/methodology). Rather than falling back toward the growth-phase average, citations held a new plateau: 7,648 on August 8 and 7,611 on August 9, averaging 7,630/day — about 26% above the prior peak. This two-day stabilization is the first evidence the recovery was not a one-day anomaly.

> The moment that surprised us wasn't the drop — it was what happened after. The domain didn't just recover to where it was. Citations held two full days above the prior peak. That tells you this isn't about content quality or domain authority at the moment of resubmission — it's about whether Bing considers a domain fresh enough to include in its citation-eligible set. Once it does, the ceiling can move higher than before.
> — Astiva AI Research Team

## What We Know vs. What We Cannot Confirm

Separating verified observations from interpretation is necessary for this study to be defensible research rather than opinion.

**What we know with confidence:** IndexNow submissions occurred on June 18 and August 7, 2026. Citations grew for 39 days after the first submission, peaking at 6,066 on July 16. Citation visibility collapsed 99.9% on July 27, reaching zero citations on August 1–2. No major content removals, indexing issues, crawlability issues, or technical SEO problems were identified during the decline. Citations recovered same-day after the August 7 resubmission and held a higher plateau on August 8–9.

**What we cannot confirm:** whether Bing changed its internal grounding logic during the period; whether retrieval systems recalibrated; whether citation-selection models changed; or whether a platform-level freshness gate tied to IndexNow submission recency is the true mechanism. The hypothesis that AI citation eligibility is influenced by a freshness/retrieval/grounding-system signal independent of traditional website-quality signals fits this one domain's data — it is not a confirmed mechanism, since Bing does not publish the rules governing AI citation eligibility.

## What Does This Mean for Brands Managing AI Visibility?

AI citations and search rankings behaved as decoupled signals throughout the study. The studied domain ranked normally in organic search, and continued to rank normally, while being entirely invisible in Bing's AI answers for two full days. Whatever mechanism kept the domain citation-eligible appears tied to a recency signal, not a quality or relevance signal.

> **Website health does not equal citation stability.** During the citation decline, the studied domain remained indexed, crawlable, accessible, technically healthy, and content-rich. Yet AI citation visibility still declined to zero before later recovering and stabilizing above its prior peak. This suggests AI citation visibility can move independently of the SEO signals brands typically track.

The cost of inaction is quantifiable: the 11-day collapse cost roughly 19,700 citations at the prior baseline run-rate. For a brand tracking AI share of voice across ChatGPT, Copilot, and Bing AI answers, that visibility is ceded to competitors filling those citation slots while an indexed, healthy domain sits at zero.

## What This Means for GEO and AI Visibility Teams

1. **Monitor trends, not snapshots.** AI citation performance should not be judged on 7-day windows alone — this study's entire collapse-to-recovery cycle played out within an 11-day span a weekly report could easily miss or misread.
2. **Separate SEO visibility from AI citation visibility.** A page can remain indexed and technically healthy while losing citation visibility in AI-generated answers entirely. Track them as distinct metrics.
3. **Expect citation volatility.** Citation visibility can rise, decline, recover, and stabilize even when the website itself is unchanged.
4. **Don't treat a citation decline as an automatic content-failure signal.** Continuing to publish and improve content rather than reacting to short-term volatility may be the correct response if the cause is a freshness signal, not a quality signal.
5. **Use longer measurement windows.** Evaluate AI citation tracking over 30-day, 60-day, and 90-day periods for a more reliable view of citation sustainability.
6. **Treat IndexNow as one contributing factor, not a guarantee.** It was the aligned trigger in this study, but it should not be read as a guaranteed driver of sustained citation volume on every domain.

## What Are the Limitations of This Study?

- **Single-domain, single-cycle observation.** The IndexNow-decay-recovery cycle was observed on one domain. Other domains may behave differently based on domain age, authority, vertical, or crawl history.
- **The 39-day decay window is one data point.** The collapse began 39 days after the June 18, 2026 IndexNow submission. This interval may vary by domain age, crawl budget, content volume, or Bing's indexing policy — none of which were controlled or tested across multiple sites in this study.
- **Only two days of stabilization data.** The August 8–9 plateau is two data points. It shows citations held above the prior peak rather than falling back immediately, but it is too short a window to confirm long-term stability.
- **Mechanism inferred, not confirmed.** Bing does not publish the rules governing AI citation eligibility. The freshness-gate interpretation fits the observed data pattern cleanly, but alternative explanations (a Bing index update, a change in citation weighting, a platform-level shift during the blackout window) cannot be fully ruled out from observational data alone. This study should be read as observed citation behavior, not proof of Bing's internal grounding and retrieval mechanisms.

## Future Research

This study raises several questions Astiva AI Research Team plans to pursue in future work:

- How does AI citation decay behave across different industries and domain authority levels?
- Do larger, more established domains recover faster from citation decay than newer ones?
- How long does citation recovery and stabilization typically take once observed?
- Does citation freshness behave differently across Bing, Google AI Overviews, ChatGPT, Perplexity, Claude, and Gemini?
- Can citation volatility be predicted from crawl, indexing, or publishing-cadence patterns?
- What is the relationship between content freshness and citation sustainability over multiple cycles?

## How Will This Finding Be Validated in Next Cycle?

The August 7, 2026 resubmission and its two-day stabilization amount to a built-in validation test, with two observable paths:

- **Path A — Cadence held.** If the team resubmits priority pages every 7–10 days going forward, the freshness hypothesis predicts citations remain elevated near or above the 7,630/day stabilization level with no collapse.
- **Path B — No further resubmission.** If no further IndexNow submission occurs, the freshness hypothesis predicts a second decay cycle around mid-September 2026 — approximately 39 days after August 7, mirroring the first cycle's decay window. Observing (or not observing) a second cliff against the same baseline is the closest this study design can get to a controlled replication.

Results for both paths will be published as a follow-up at [astiva.ai/research](https://astiva.ai/research).

## Related Reading

For a general definition of AI citation decay, its common causes, warning signs, and a step-by-step diagnostic and response framework — beyond this single study — see [What Is AI Citation Decay?](./what-is-ai-citation-decay-explained.md), which uses this study as a primary source.

## Glossary

- **AI Citation Decay** — A measurable decline in how often a page or domain is displayed as a cited source in monitored AI-generated answers over time.
- **Grounding Index** — The retrieval layer an AI system draws from to select and cite sources for generated answers.
- **IndexNow** — A free, open protocol that lets a website instantly notify participating search engines (including Bing) that a URL was added, updated, or removed.
- **Citation Freshness** — A hypothesized recency signal governing whether a domain remains eligible for AI citation, distinct from content quality or search ranking signals.
- **Cited-Page Breadth** — The number of distinct pages appearing as cited sources on a given day.
- **Freshness Gate** — The working hypothesis that AI citation eligibility can be gated by a recency signal independent of content quality or organic search rankings.
- **Detect → Diagnose → Displace → Prove Cycle** — Astiva AI's operating framework for finding, fixing, and proving AI citation performance. See [framework.md](./framework.md) and [astiva.ai/methodology](https://astiva.ai/methodology) for the full specification.

## Sources

1. Bing Webmaster Tools, AI Performance Overview — daily export for an anonymized B2B SaaS brand, June 18 – August 9, 2026. Data on file.
2. IndexNow official documentation — [indexnow.org/documentation](https://www.indexnow.org/documentation)
3. Bing IndexNow documentation — [bing.com/webmasters/indexnow](https://www.bing.com/webmasters/indexnow)
4. Full study — [astiva.ai/research/ai-citation-decay-bing-grounding-index](https://astiva.ai/research/ai-citation-decay-bing-grounding-index)
5. Companion explainer — [What Is AI Citation Decay?](https://astiva.ai/blog/what-is-ai-citation-decay)
