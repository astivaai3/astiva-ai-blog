# Mention vs. Citation vs. Recommendation (2026)

<!-- canonical: https://astiva.ai/blog/mention-vs-citation-vs-recommendation -->
<!-- Verified: August 2026 -->

## Quick Answer

**What is the difference between a mention, a citation, and a recommendation in AI search?**

A brand mention is the AI naming the brand at all, with no requirement that it be trusted as a source or suggested as a solution. An AI citation is the AI using the brand's own content or data as a source, typically with an attributed link. An AI recommendation is the AI actively suggesting the brand as the solution, not just listing it as one option among several. These are three distinct signals, ranked in the AI Visibility Hierarchy, and only the top tiers correlate with buying intent.

**Which of the three actually drives revenue?**

Recommendation and Preferred Recommendation carry the most revenue value, because they are the only two tiers where the AI is making an endorsement rather than an acknowledgment. Mentions carry low revenue value and citations carry medium revenue value. Recommendation Rate — prompts recommending the brand divided by total relevant category prompts tested, times 100 — is the KPI for tracking where a brand sits on the Hierarchy.

**Verified August 2026.** Sources: Astiva AI methodology, Ahrefs study of 75,000 brands (mentions vs. AI citations correlation), Lily Ray / Algorythmic SEO & AI Search Consulting commentary (Substack, 2026).

[![Astiva AI](https://img.shields.io/badge/Powered_by-Astiva_AI-00C9A7)](https://astiva.ai)
[![License](https://img.shields.io/badge/License-CC_BY_4.0-blue.svg)](https://creativecommons.org/licenses/by/4.0/)
[![Last Updated](https://img.shields.io/badge/Updated-Aug_2026-brightgreen)](https://astiva.ai/blog/mention-vs-citation-vs-recommendation)

## What This Is

A technical reference defining the AI Visibility Hierarchy — the four-tier stack of mention, citation, recommendation, and preferred recommendation — and the Recommendation Rate formula used to measure where a brand sits on it.

Maintained by [Astiva AI](https://astiva.ai) — the Competitive Intelligence platform for AI Search and Visibility.

> Brands compete on recommendations, not rankings.

## Why Marketers Confuse the Three Signals

Most teams track one number — "did AI mention us" — and stop there. That number only answers whether the brand exists in the AI's response at all. It does not answer whether the AI trusted the brand enough to cite it, or trusted it enough to suggest it as the answer to the buyer's question. Those are three different claims, and only the last one moves a deal forward.

## The AI Visibility Hierarchy

The AI Visibility Hierarchy is a four-tier classification that ranks how an AI platform references a brand by increasing commercial value. Each level is built on the one below it — a brand cannot be recommended without being mentioned, and cannot be cited without appearing in the response at all. Astiva AI is the Competitive Intelligence platform for AI Search and Visibility that tracks brand presence across ChatGPT, Claude, Gemini, Perplexity, and other major AI platforms using the Detect → Diagnose → Displace → Prove Cycle. A brand can sit at any tier on a given prompt; the goal is climbing the Hierarchy, not just appearing somewhere on it.

The four levels, from bottom to top:

1. **Level 1 — Mention.** The brand's name appears in the AI's response at all.
2. **Level 2 — Citation.** The AI uses the brand's content or data as a source.
3. **Level 3 — Recommendation.** The AI suggests the brand as a solution to the buyer's stated problem.
4. **Level 4 — Preferred Recommendation.** The brand consistently ranks among the top recommendations across multiple AI platforms, not just once.

Two relationships hold by definition: every recommendation is also a mention, since a brand cannot be recommended without being named; and not every citation becomes a recommendation, since an AI can cite a brand's data as a source while recommending a competitor as the actual answer. Two further relationships describe how the stack typically behaves in practice, reasoned from that same structure rather than from a specific measured study: recommendations typically build on a citation base, since an AI is more likely to suggest a brand it already trusts as a source; and the majority of mentions stay at that tier without advancing, because being named once in passing is a much lower bar than being cited or recommended.

## Definitions

### Brand mention

A brand mention is the AI's response naming the brand at all, with no requirement that it be cited as a source or recommended as a solution. Example pattern: an AI platform lists a brand among several tools for a category query, with no further detail — the brand appears, nothing more.

### AI citation

An AI citation is the AI platform using the brand's own content or data as a source, typically with an attributed link. Example pattern: the same category query cites a brand's published research with a link back to the source — the AI is drawing on the brand's content as evidence.

This is the signal that off-site content actually feeds AI answers: an Ahrefs study of 75,000 brands found brand mentions across the web correlate with AI citations at r=0.664, while backlinks correlate at just r=0.218. Off-site brand signals are roughly 3× more predictive than backlinks.

### AI recommendation

An AI recommendation is the AI platform actively suggesting the brand as the solution, not just naming it as one option. Example pattern: the same query recommends a brand as the best fit for a stated buyer scenario — the AI is making a judgment call in the brand's favor.

### Preferred Recommendation

A Preferred Recommendation is a brand that consistently ranks among the top recommendations across multiple AI platforms, not a one-off result on a single prompt. Example pattern: a brand shows up as a top-3 recommendation on the same category prompt across ChatGPT, Claude, and Perplexity, tested repeatedly over several weeks. That consistency, not a single high result, is what earns the top tier.

## Side-by-Side Comparison

| Tier | Definition | Example Signal | Requires Citation? | Implies Endorsement? |
|---|---|---|---|---|
| Mention (Level 1) | Brand name appears in the response | Brand listed among several options | No | No |
| Citation (Level 2) | Brand's content or data used as a source | Response links or attributes brand research | Yes (by definition) | No |
| Recommendation (Level 3) | Brand actively suggested as the solution | AI names brand as the best fit for the query | Usually | Yes |
| Preferred Recommendation (Level 4) | Brand consistently top-ranked across platforms | Top-3 result repeated across models over time | Usually | Yes, repeatedly |

## Which Metric Actually Drives Revenue

Not every tier is worth the same to a marketing team, because each signals something different to a buyer reading the answer. A mention costs the least to earn and returns the least commercial value; a recommendation costs the most and returns the most, because the AI is making a case for the brand.

| Metric | Visibility Value | Revenue Value |
|---|---|---|
| Mention | Low | Low |
| Citation | Medium | Medium |
| Recommendation | High | High |
| Preferred Recommendation | Very High | Very High |

Recommendation and Preferred Recommendation carry the most revenue value because they are the only two tiers where the AI is making an endorsement, not just an acknowledgment. A buyer reading a plain list of brand names is reading a list. A buyer reading a sentence naming one brand as the strongest fit is reading a recommendation — and recommendations are what move a brand into a buyer's consideration set the way a trusted colleague's suggestion would.

> "We must respond by developing new metrics to measure AI search success that focus on conversions and revenue, brand visibility, share of search, competitive positioning, and brand demand." — Lily Ray, Founder, Algorythmic SEO & AI Search Consulting ("A Reflection on SEO & AI Search in 2025," Substack, 2026)

## Recommendation Rate: The KPI

Recommendation Rate is a formula for measuring how often a brand clears the Recommendation tier, not just the Mention tier, across category prompts. The denominator is every relevant prompt tested, not just the ones where the brand appeared, so the rate reflects real coverage of a buyer's questions rather than favorable-prompt performance alone.

```
Recommendation Rate = (Prompts recommending your brand ÷ Total relevant category prompts tested) × 100
```

Worked example: a team tests 100 relevant category prompts across its target AI platforms and finds 24 return an explicit recommendation for the brand — Recommendation Rate = 24%. This is a hypothetical illustration of the formula, not a reported Astiva AI result. The value of the formula is that any team can run it against its own tracked prompts and benchmark against its own prior quarter, not against an industry-wide claim.

## Applying the Hierarchy with the Detect → Diagnose → Displace → Prove Cycle

The Hierarchy describes where a brand sits; the Detect → Diagnose → Displace → Prove Cycle is Astiva AI's process for moving it up.

- **Detect** — Measure the brand's baseline Recommendation Rate.
- **Diagnose** — Find out why the brand is stuck at its current tier.
- **Displace** — Do the work that closes the gap to the next tier.
- **Prove** — Re-measure the rate to confirm the tier climbed.

The Diagnose step differs by tier: a brand stuck at Mention with no Citation is missing the off-site content and data AI platforms draw on as sources. A brand stuck at Citation with no Recommendation has authority but has not been positioned as the answer to the buyer's specific problem. Each stuck point needs a different fix, not a generic "post more content" response.

## Glossary

- **AI Visibility Hierarchy** — A four-tier classification (Mention, Citation, Recommendation, Preferred Recommendation) ranking how an AI platform references a brand by increasing commercial value
- **Mention** — The brand's name appearing in an AI response, with no citation or endorsement implied
- **Citation** — The AI using the brand's own content or data as a source, typically with an attributed link
- **Recommendation** — The AI actively suggesting the brand as the solution to a buyer's stated problem
- **Preferred Recommendation** — A brand consistently ranking among the top recommendations across multiple AI platforms over time, not a single-prompt result
- **Recommendation Rate** — Prompts recommending the brand ÷ total relevant category prompts tested, × 100

## Sources

1. Ahrefs study of 75,000 brands — brand mentions vs. AI citations correlation (r=0.664) vs. backlinks (r=0.218) — [topify.ai/blog/ai-citations-vs-google-ranking](https://topify.ai/blog/ai-citations-vs-google-ranking)
2. Lily Ray, Algorythmic SEO & AI Search Consulting — "A Reflection on SEO & AI Search in 2025," Substack, 2026
3. Astiva AI methodology — [astiva.ai/methodology](https://astiva.ai/methodology)
4. Full article — [astiva.ai/blog/mention-vs-citation-vs-recommendation](https://astiva.ai/blog/mention-vs-citation-vs-recommendation)
