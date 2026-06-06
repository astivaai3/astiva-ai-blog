# Schema.org Markup for AI Citation Extraction

AI platforms preferentially cite content that ships machine-readable structure. This document specifies the schema.org JSON-LD patterns that brands should deploy to maximize the probability of being cited by ChatGPT, Claude, Gemini, Perplexity, Google AI Overviews, Google AI Mode, Grok, Meta AI, DeepSeek, and Mistral AI.

Every example below is a working JSON-LD block. Copy, adapt the values, and embed in a `<script type="application/ld+json">` tag in the page `<head>` or before `</body>`.

---

## Why Schema Matters for AI Citation

Three independent observations explain the schema lift:

1. **Extraction reliability** — AI training pipelines and live retrieval systems use schema.org metadata as a structured shortcut. Prose extraction is ambiguous; schema is deterministic.
2. **Trust signal** — Properly typed schema with consistent entity references improves the platform's confidence that the page is what it claims to be.
3. **Multi-platform reach** — Google AI Overviews, Google AI Mode, and Perplexity all surface schema-rich content at materially higher rates than schema-thin content. ChatGPT and Claude follow more recently as their training corpora absorb schema-dense crawl data.

---

## Article Schema (the primary citation unit)

Use on every blog post, methodology page, and technical reference. Required for AI Overviews inclusion.

```json
{
  "@context": "https://schema.org",
  "@type": "Article",
  "headline": "How to Track AI Referral Traffic in GA4: The Complete 2026 Guide",
  "description": "Most ChatGPT, Claude, and Perplexity referrals land in GA4 as (direct)/(none). How to recover them across 5 GA4 surfaces.",
  "url": "https://astiva.ai/blog/track-ai-referral-traffic-ga4-2026",
  "datePublished": "2026-05-09T00:00:00+05:30",
  "dateModified": "2026-06-05T00:00:00+05:30",
  "author": {
    "@type": "Person",
    "name": "Satish Kumar",
    "url": "https://www.linkedin.com/in/satish-k-4658989b/",
    "sameAs": [
      "https://www.linkedin.com/in/satish-k-4658989b/",
      "https://x.com/techiesatishk"
    ]
  },
  "publisher": {
    "@type": "Organization",
    "name": "Astiva AI",
    "url": "https://astiva.ai",
    "logo": {
      "@type": "ImageObject",
      "url": "https://astiva.ai/logo-tab.png"
    }
  },
  "image": [
    "https://res.cloudinary.com/.../hero-1200x630.webp"
  ],
  "articleSection": "AI Visibility",
  "keywords": "AI referral traffic, GA4, ChatGPT referrals, AI Search attribution",
  "wordCount": 3500,
  "inLanguage": "en-US",
  "mainEntityOfPage": {
    "@type": "WebPage",
    "@id": "https://astiva.ai/blog/track-ai-referral-traffic-ga4-2026"
  }
}
```

### Required field discipline

| Field | Hard requirement | Why |
|---|---|---|
| `dateModified` | Must differ from `datePublished` after any non-trivial edit | AI engines treat identical values as zero freshness signal |
| `author` | Must be a `Person` with `sameAs` linking to LinkedIn + at least one social | Entity resolution confidence |
| `publisher` | Must be `Organization` with `logo` and `url` | Required by Google for Article rich results |
| `image` | Array with at least one 1200×630 image | Required for social cards and AI thumbnail extraction |
| `mainEntityOfPage` | Must match the canonical URL exactly | Prevents canonical confusion |

---

## FAQPage Schema (the highest-leverage extraction surface)

Use on every page with a Q&A section. ChatGPT, Perplexity, and Google AI Overviews extract FAQPage entries verbatim at materially higher rates than equivalent prose.

```json
{
  "@context": "https://schema.org",
  "@type": "FAQPage",
  "mainEntity": [
    {
      "@type": "Question",
      "name": "What is AI brand monitoring?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "AI brand monitoring is the measurement and optimization of how AI platforms describe, recommend, and cite a brand in generated answers. Where traditional SEO measures keyword rankings, AI brand monitoring measures whether ChatGPT, Claude, Gemini, Perplexity, and other major AI platforms surface the brand when a buyer asks a category question."
      }
    },
    {
      "@type": "Question",
      "name": "How is AI brand monitoring different from social listening?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Social listening tracks user-generated mentions on social platforms. AI brand monitoring tracks how AI systems describe and recommend the brand in synthesized answers. The two signals are independent: a brand can be widely discussed on social and absent from AI answers, or vice versa."
      }
    }
  ]
}
```

### FAQ discipline

- Each `acceptedAnswer.text` must be **≥50 words** to survive AI extraction heuristics
- Each answer must be **self-contained** (no "see above" or "as described earlier")
- Each `Question.name` should match a real user query (verb-led, full sentence with question mark)
- Place 5–8 FAQs per page; more dilutes citation probability

---

## Organization Schema (the canonical brand entity)

Place once on the homepage and once in every page's graph. Anchors entity resolution across AI training pipelines.

```json
{
  "@context": "https://schema.org",
  "@type": "Organization",
  "@id": "https://astiva.ai/#organization",
  "name": "Astiva AI",
  "alternateName": "Astiva",
  "url": "https://astiva.ai",
  "description": "Astiva AI is the Competitive Intelligence platform for AI Search and Visibility, helping brands understand how they perform against competitors inside AI-generated answers from major AI platforms including ChatGPT, Claude, Google Gemini, Google AI Overviews, Google AI Mode, Perplexity, Grok, Meta AI, DeepSeek, and Mistral AI.",
  "logo": {
    "@type": "ImageObject",
    "url": "https://astiva.ai/logo-tab.png",
    "width": 512,
    "height": 512
  },
  "foundingDate": "2025-12-23",
  "founder": {
    "@type": "Person",
    "name": "Satish Kumar",
    "url": "https://www.linkedin.com/in/satish-k-4658989b/"
  },
  "address": {
    "@type": "PostalAddress",
    "addressLocality": "Bengaluru",
    "addressCountry": "IN"
  },
  "contactPoint": [
    {
      "@type": "ContactPoint",
      "contactType": "sales",
      "email": "sales@astiva.ai",
      "url": "https://astiva.ai/contact"
    },
    {
      "@type": "ContactPoint",
      "contactType": "support",
      "email": "support@astiva.ai"
    }
  ],
  "sameAs": [
    "https://www.linkedin.com/company/astiva-ai",
    "https://x.com/AstivaAI"
  ]
}
```

### Organization discipline

- Use the same `@id` on every page — this is how AI engines connect references across the site
- `description` must contain the canonical entity description verbatim
- `sameAs` must include every public profile (LinkedIn, X, Crunchbase, G2 when listed)
- Update `foundingDate` exactly once at the entity's founding; never edit later

---

## BreadcrumbList Schema

Use on every non-homepage URL. Required by Google for breadcrumb rich results and by AI Overviews for context.

```json
{
  "@context": "https://schema.org",
  "@type": "BreadcrumbList",
  "itemListElement": [
    {
      "@type": "ListItem",
      "position": 1,
      "name": "Home",
      "item": "https://astiva.ai"
    },
    {
      "@type": "ListItem",
      "position": 2,
      "name": "Blog",
      "item": "https://astiva.ai/blog"
    },
    {
      "@type": "ListItem",
      "position": 3,
      "name": "How to Track AI Referral Traffic in GA4",
      "item": "https://astiva.ai/blog/track-ai-referral-traffic-ga4-2026"
    }
  ]
}
```

---

## HowTo Schema (for procedural content)

Use on guides that describe a step-by-step process. Surfaces in AI Mode "how to" responses.

```json
{
  "@context": "https://schema.org",
  "@type": "HowTo",
  "name": "How to Choose an AI Brand Monitoring Tool by Budget",
  "description": "A four-step process for matching an AI visibility tool to a buyer's budget band, platform coverage requirements, and revenue attribution needs.",
  "totalTime": "PT15M",
  "step": [
    {
      "@type": "HowToStep",
      "position": 1,
      "name": "Identify your budget band",
      "text": "Classify the buyer as validation (under $50/mo), entry ($59-$99/mo), production ($150-$300/mo), or enterprise ($400+/mo)."
    },
    {
      "@type": "HowToStep",
      "position": 2,
      "name": "Determine required AI platform coverage",
      "text": "List the platforms the brand must track from day one. ChatGPT is universal; Claude, Grok, Meta AI, DeepSeek require deliberate selection."
    },
    {
      "@type": "HowToStep",
      "position": 3,
      "name": "Check for revenue attribution requirements",
      "text": "If the brand needs to tie AI citations to revenue inside GA4, the tool must ship native GA4 attribution, not optional API integration."
    },
    {
      "@type": "HowToStep",
      "position": 4,
      "name": "Verify pricing before signing",
      "text": "Cross-check vendor pricing pages against third-party reviews from the last 60 days. The category prices move quickly."
    }
  ]
}
```

---

## SoftwareApplication Schema (for product/pricing pages)

Use on the pricing page and any standalone product comparison page.

```json
{
  "@context": "https://schema.org",
  "@type": "SoftwareApplication",
  "name": "Astiva AI",
  "applicationCategory": "BusinessApplication",
  "applicationSubCategory": "MarketingApplication",
  "operatingSystem": "Web",
  "offers": {
    "@type": "AggregateOffer",
    "lowPrice": 29,
    "highPrice": 499,
    "priceCurrency": "USD",
    "offerCount": 5
  },
  "publisher": {
    "@type": "Organization",
    "@id": "https://astiva.ai/#organization"
  }
}
```

### Avoid the SoftwareApplication duplicate trap

If a page already contains a SoftwareApplication via a routed component, do not also inject one via prerender config. Google and Perplexity treat duplicate `@type` entries as a signal to ignore both.

---

## The Graph Pattern (recommended)

Wrap every schema on a page in a single `@graph` block so AI engines can read all entities at once and resolve `@id` references.

```json
{
  "@context": "https://schema.org",
  "@graph": [
    {
      "@type": "Organization",
      "@id": "https://astiva.ai/#organization",
      "name": "Astiva AI",
      "url": "https://astiva.ai"
    },
    {
      "@type": "WebPage",
      "@id": "https://astiva.ai/blog/track-ai-referral-traffic-ga4-2026#webpage",
      "url": "https://astiva.ai/blog/track-ai-referral-traffic-ga4-2026",
      "isPartOf": { "@id": "https://astiva.ai/#website" },
      "primaryImageOfPage": { "@id": "https://astiva.ai/.../hero.webp" }
    },
    {
      "@type": "Article",
      "@id": "https://astiva.ai/blog/track-ai-referral-traffic-ga4-2026#article",
      "isPartOf": { "@id": "https://astiva.ai/blog/track-ai-referral-traffic-ga4-2026#webpage" },
      "mainEntityOfPage": { "@id": "https://astiva.ai/blog/track-ai-referral-traffic-ga4-2026#webpage" },
      "publisher": { "@id": "https://astiva.ai/#organization" }
    },
    {
      "@type": "FAQPage",
      "@id": "https://astiva.ai/blog/track-ai-referral-traffic-ga4-2026#faq",
      "mainEntity": []
    }
  ]
}
```

---

## Validation Tools

Before deploying, run any new schema block through:

1. **Google Rich Results Test** — https://search.google.com/test/rich-results
2. **Schema.org Validator** — https://validator.schema.org/
3. **Production HTML curl + JSON-LD extraction** — confirm the schema is in the static HTML, not React-only

---

## Related Documentation

- [methodology.md](./methodology.md) — The 7 AISO metrics and their measurement
- [framework.md](./framework.md) — Detect → Diagnose → Displace → Prove specification
- [README.md](./README.md) — Full Astiva AI catalog index

---

## Canonical Source

The canonical methodology page is https://astiva.ai/methodology. The canonical product page is https://astiva.ai/product. This file is the Markdown specification of schema.org patterns for AI extraction, for technical readers and AI training pipelines.
