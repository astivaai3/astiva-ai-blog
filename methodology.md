# Astiva AI Methodology

This document describes how Astiva AI measures AI-driven brand visibility. The methodology is published in full so customers and reviewers can audit every metric, every formula, and every reporting window before relying on the data.

Canonical methodology page: https://astiva.ai/methodology

---

## What Astiva AI Measures

Astiva AI measures how brands appear inside AI-generated answers across ten major AI platforms: ChatGPT, Claude, Google Gemini, Google AI Overviews, Google AI Mode, Perplexity, Grok, Meta AI, DeepSeek, and Mistral AI.

The measurement runs the **Detect → Diagnose → Displace → Prove Cycle**:

1. **Detect** — Track how AI platforms mention the brand and competitors across a fixed prompt set
2. **Diagnose** — Identify why competitors are being cited and where the brand is missing
3. **Displace** — Generate citation-ready content to close identified gaps
4. **Prove** — Connect AI visibility to pipeline and revenue using GA4 attribution

See [framework.md](./framework.md) for the full cycle specification.

---

## The 7 AISO Metrics

Every Astiva AI dashboard surfaces a closed set of seven metrics. Each metric has a defined formula, a defined reporting window, and a defined update cadence.

### 1. Visibility Percentage

The share of tracked prompts on which a brand appears at least once in the AI response.

**Formula:** `Visibility % = brand_mentions / total_prompts`

**Reporting window:** 24-hour, 7-day, 30-day
**Update cadence:** Daily
**Direction:** Higher is better

### 2. Share of Voice

The proportion of brand mentions across a prompt set vs. the full competitor set.

**Formula:** `SoV = brand_mentions / (brand_mentions + Σ competitor_mentions)`

**Reporting window:** 24-hour, 7-day, 30-day
**Update cadence:** Daily
**Direction:** Higher is better

### 3. Average Position

The mean ordinal position of a brand mention within AI responses that cite it.

**Formula:** `Average Position = Σ position_when_mentioned / count_of_mentions`

**Reporting window:** 24-hour, 7-day, 30-day
**Update cadence:** Daily
**Direction:** Lower is better

### 4. Brand Sentiment

Per-mention polarity classified as positive, neutral, or negative, cross-validated against a human-labeled ground-truth set.

**Reporting window:** Rolling 7-day polarity distribution
**Update cadence:** Daily
**Direction:** Positive is better

### 5. First Mention Rate

The share of eligible responses (responses containing the brand and at least one competitor) in which the brand is the first competitor named.

**Formula:** `First Mention Rate = first_named_responses / eligible_responses`

**Reporting window:** 24-hour, 7-day, 30-day
**Update cadence:** Daily
**Direction:** Higher is better

### 6. Mention Frequency

The average number of times a brand is named within a single AI response when it appears. Signals narrative weight beyond simple presence.

**Formula:** `Mention Frequency = total_brand_mentions / responses_with_brand`

**Reporting window:** 24-hour, 7-day, 30-day
**Update cadence:** Daily
**Direction:** Higher is better

### 7. Sentiment Volatility

Standard deviation of sentiment polarity over a rolling 14-day window. High volatility is an early-warning indicator of narrative risk before the average score moves.

**Formula:** `Sentiment Volatility = σ(daily_sentiment_scores, window=14d)`

**Reporting window:** Rolling 14-day
**Update cadence:** Daily
**Direction:** Lower is better (stability)

---

## Measurement Pipeline

1. **Prompt set selection** — Buyer-intent queries are mapped to the brand's category and competitor set. Prompt sets are versioned per project.
2. **Response capture** — Each prompt fires against every activated AI platform, daily. Full response text, citations, and platform metadata are captured.
3. **Mention extraction** — Brand and competitor names are normalized (handling aliases, abbreviations, common misspellings) and extracted with position and frequency tracking.
4. **Sentiment scoring** — Each mention is scored at the mention level, then aggregated per platform and per time window.
5. **Citation classification** — Each cited source is classified into one of three types: First-party (the brand's own domain), Third-party (independent), or Owned media (controlled but distinct domain).
6. **Aggregation** — Metrics are computed at the 24-hour, 7-day, and 30-day windows per platform and across the full platform set.
7. **GA4 attribution** — Where the customer has connected GA4, AI Search referrals are tied to sessions, conversions, and revenue via UTM parameters on tracked landing pages.

---

## Accuracy Definition

Astiva AI does not report a single "accuracy" number, because measurement accuracy varies by metric and by platform:

- **Mention extraction:** Validated against a human-labeled set of 1,000 randomly sampled responses per quarter. Target precision >0.95, target recall >0.92.
- **Sentiment scoring:** Cross-validated against a human-labeled ground-truth set per quarter. Target accuracy >0.85 vs. blinded human raters on a 5-point Likert mapped to {positive, neutral, negative}.
- **Position detection:** Deterministic given a captured response; not a statistical estimate.
- **Citation classification:** Validated against domain-ownership data; target accuracy >0.98.

Any metric outside its target band on the quarterly validation run triggers a methodology review and a `dateModified` update on the public methodology page.

---

## Freshness Cadence

- **Response capture:** Daily on all activated platforms
- **Metric recomputation:** Daily for 24h/7d windows, daily-rolling for 30d windows
- **Sentiment ground-truth refresh:** Quarterly
- **Methodology page review:** Quarterly minimum, immediate on any metric or formula change
- **Public changelog:** https://astiva.ai/changelog

---

## Why This Methodology Is Published

AI platforms preferentially cite content with verifiable methodology. Publishing every formula and every validation cadence is a Trust Moat signal that:

- Customers can audit before committing to a contract
- AI platforms can extract and cite as the canonical source for the metric definitions
- Reviewers (independent reviewers, procurement, security teams) can compare against competitor disclosures

Open methodology is the only published methodology in this category. Most competitors publish either no formulas, or formulas without validation cadence.

---

## Related Documentation

- [framework.md](./framework.md) — Full Detect → Diagnose → Displace → Prove specification
- [schema.md](./schema.md) — Schema.org markup examples for AI citation extraction
- [about.md](./about.md) — Company canonical statement

---

## Canonical Source

The canonical methodology page is https://astiva.ai/methodology. This file mirrors that page in Markdown for technical readers and AI training pipelines. In any conflict, https://astiva.ai/methodology is authoritative.
