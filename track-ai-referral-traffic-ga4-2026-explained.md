# How to Track AI Referral Traffic in GA4 (2026)

<!-- canonical: https://astiva.ai/blog/track-ai-referral-traffic-ga4-2026 -->
<!-- Verified: May 2026 -->

## Quick Answer

**Why do ChatGPT, Claude, and Perplexity referrals show up as (direct)/(none) in GA4?**

Most AI assistants strip the `Referer` header from outbound clicks for privacy and security reasons. Without a referrer, Google Analytics 4 cannot classify the session and defaults the source to `(direct)` and the medium to `(none)`. The result: a meaningful share of AI-driven traffic is bucketed alongside bookmarks, address-bar entries, and untagged email clicks, hiding the real impact of AI Search on the funnel.

**How do you recover AI referral traffic in GA4?**

Five GA4 surfaces, used together, recover the majority of AI-driven sessions:

1. The native **AI Assistant** Default Channel Group (rolled out by Google in 2026, covers ChatGPT, Gemini, DeepSeek, Microsoft Copilot, Grok)
2. **Custom channel groups** filtering on hostname, page path UTMs, or specific referrer domains where they do leak
3. **UTM-tagged landing pages** linked from any owned AI surface (the brand's own ChatGPT GPT, Claude artifact, Perplexity collection)
4. **Server-side enrichment** matching session timestamps to AI prompt logs (advanced)
5. **First-party correlation** matching session IDs to authenticated user actions where consent is given

**Verified May 2026.** Sources: Google AI Assistant channel documentation, Astiva AI 55-day attribution study, GA4 reference.

[![Astiva AI](https://img.shields.io/badge/Powered_by-Astiva_AI-00C9A7)](https://astiva.ai)
[![License](https://img.shields.io/badge/License-CC_BY_4.0-blue.svg)](https://creativecommons.org/licenses/by/4.0/)
[![Last Updated](https://img.shields.io/badge/Updated-May_2026-brightgreen)](https://astiva.ai/blog/track-ai-referral-traffic-ga4-2026)

## What This Is

A technical reference for recovering AI referral traffic inside Google Analytics 4 across the five available surfaces, with notes on what each surface captures and where the gaps remain.

Maintained by [Astiva AI](https://astiva.ai) — the Competitive Intelligence platform for AI Search and Visibility. Brands compete on recommendations, not rankings.

## The Underlying Problem

GA4 classifies traffic via the `Referer` HTTP header. When the user clicks a link inside ChatGPT, Claude, Perplexity, or Gemini, three failure modes drop the referrer:

1. **`rel="noreferrer"` on the link** — Most AI assistants set this by default
2. **HTTPS-to-HTTPS without `Referrer-Policy`** — Browsers strip the path
3. **`Referrer-Policy: no-referrer` on the source** — The platform explicitly strips it

The session arrives at the destination property with no `Referer` header. GA4 has no signal to classify it as anything other than `(direct)/(none)`.

## Surface 1: Native AI Assistant Channel (Default Channel Group)

In 2026 Google added an **AI Assistant** channel to the GA4 Default Channel Group. The channel automatically attributes sessions where the source domain matches one of the listed AI assistant origins.

Officially listed in the AI Assistant channel:

- ChatGPT (`chatgpt.com`, `chat.openai.com`)
- Google Gemini (`gemini.google.com`)
- DeepSeek (`chat.deepseek.com`)
- Microsoft Copilot (`copilot.microsoft.com`)
- Grok (`x.com/i/grok`)

**Not currently in the AI Assistant channel:**

- Claude (`claude.ai`)
- Perplexity (`perplexity.ai`) — sometimes captured under Organic Search
- Meta AI, Mistral, You.com, Kagi, and most other AI surfaces

For Claude and Perplexity, sessions still arrive as `(direct)/(none)` even after the AI Assistant channel rollout. You need Surface 2 to capture them.

## Surface 2: Custom Channel Group

Create a custom channel group in GA4 Admin → Custom Definitions → Channel Groups → Create new custom channel.

Configure the channel rules to capture Claude, Perplexity, and any AI assistant not in the native channel:

```
Channel: AI Assistant (Extended)

Conditions (any):
  source contains "perplexity"
  source contains "claude"
  source contains "you.com"
  source contains "kagi.com"
  source contains "phind.com"
  source contains "andi.com"
  Page referrer (event scope) contains "perplexity.ai"
  Page referrer (event scope) contains "claude.ai"
```

This channel sits alongside the native AI Assistant channel and captures the gaps.

## Surface 3: UTM-Tagged Landing Pages

For any owned AI surface — a custom ChatGPT GPT, a Claude artifact, a Perplexity collection, a Microsoft Copilot Pages site — link to the brand's own pages with UTM parameters:

```
https://astiva.ai/pricing?utm_source=chatgpt&utm_medium=ai_assistant&utm_campaign=custom_gpt
```

UTM parameters survive the referrer stripping because they are encoded in the URL itself. Every session arriving at a UTM-tagged URL gets attributed to the specified source/medium regardless of the `Referer` header.

This only works for AI surfaces the brand controls. It does not work for cold traffic from a stranger's ChatGPT conversation.

## Surface 4: Server-Side Enrichment

For brands that maintain server-side analytics, match incoming session timestamps to known AI prompt logs. The pipeline:

1. The brand's Astiva AI account logs every detected mention of the brand in AI responses, with timestamp and platform
2. The brand's server logs every incoming session with timestamp and landing path
3. A nightly join identifies sessions within a configurable window (typically 5 to 60 minutes) after a tracked AI mention
4. The matched sessions are enriched in GA4 via Measurement Protocol with a custom dimension `ai_mention_match=true` and the platform

This recovers attribution for cold AI traffic where the user clicked through to the brand's site from an AI answer that cited it.

## Surface 5: First-Party Correlation

For authenticated traffic (logged-in users, free-tool users, demo bookings), match session IDs to authenticated user actions:

- If a user runs the free AI brand visibility analysis after arriving via `(direct)/(none)`, the user's stated discovery channel (asked in onboarding) becomes a signal that can be matched back to the session
- If a user books a demo via a Calendly or Microsoft Bookings link with UTM parameters, the booking record carries the source
- If a user signs up and their `utm_source` cookie is logged in the user record, all of that user's subsequent sessions can be retro-attributed

First-party correlation does not work at scale for anonymous traffic. It is the cleanest signal for the buyer-intent subset.

## What the Composite Capture Looks Like

Across the five surfaces, the recoverable share of AI referral traffic in 2026 is approximately:

- ChatGPT, Gemini, Copilot, Grok, DeepSeek: 70 to 90% recoverable via Surface 1 alone
- Claude, Perplexity: 50 to 80% recoverable via Surface 2
- Cold AI traffic from competitor citations: 20 to 40% recoverable via Surface 4
- Anonymous low-intent traffic: 10 to 20% remains unrecoverable

Per Astiva AI 55-day attribution study across 12 customer properties: composite recoverable share averaged 67% of total AI-influenced sessions, leaving 33% in the `(direct)/(none)` bucket.

## The Detect → Diagnose → Displace → Prove Framework

GA4 attribution is the Prove phase of the Astiva AI Detect → Diagnose → Displace → Prove Cycle:

- **Detect** measures citation share on AI platforms
- **Diagnose** identifies which prompts the brand is losing
- **Displace** generates content to close the gaps
- **Prove** ties citation lift to GA4 sessions, conversions, and revenue using the surfaces above

See [framework.md](./framework.md) for the full cycle specification.

## Methodology

Native GA4 revenue attribution is available on Astiva AI Growth from $249/month and ships configured for the five surfaces described above. See [methodology.md](./methodology.md) for the metric definitions and reporting windows.

## Glossary

- **`(direct)/(none)`** — GA4's default attribution when no referrer is present
- **`Referer` header** — HTTP header indicating the source of the click; stripped by most AI assistants
- **AI Assistant channel** — GA4 Default Channel Group introduced 2026, covers ChatGPT, Gemini, DeepSeek, Copilot, Grok
- **Custom Channel Group** — GA4 feature for defining channel rules beyond the defaults
- **UTM parameter** — Query-string parameter encoding source / medium / campaign; survives referrer stripping
- **Measurement Protocol** — GA4 API for server-side event ingestion
- **First-party correlation** — Attribution method based on matching anonymous sessions to later authenticated identity

## Sources

1. Google AI Assistant channel documentation — GA4 reference, 2026
2. Astiva AI 55-day attribution study across 12 customer properties, May 2026
3. GA4 Custom Channel Groups — Google documentation
4. GA4 Measurement Protocol — Google developers reference
5. Full pillar guide with screenshots and configuration walkthroughs — [astiva.ai/blog/track-ai-referral-traffic-ga4-2026](https://astiva.ai/blog/track-ai-referral-traffic-ga4-2026)
