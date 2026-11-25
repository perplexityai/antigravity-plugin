---
name: perplexity-search
description: >-
  Search the live web, look up current documentation or error reports, get
  cited answers, run web-grounded reasoning, or conduct deep multi-source
  research using Perplexity API MCP tools. Use whenever a task requires
  up-to-date facts, primary sources, library docs, recent releases, or
  verified citations beyond local workspace files.
---

# Perplexity Web Search & Research

Use Perplexity's hosted MCP tools to ground answers, verify current facts, and research technical or business topics with citations.

## Core Rule: Pick One Tool and Stop Once Answered

Choose the single fastest tool that fits the question. Do not chain `perplexity_search` and `perplexity_ask` for the same lookup: if `perplexity_search` snippets already answer the question, synthesize directly from them without calling `perplexity_ask`. Only issue a second call when the first result is missing a required fact or needs a different query.

## Choosing the Right Tool

| Need | Tool | Latency & Behavior |
|---|---|---|
| Live lookup, current facts (weather, scores, prices, releases), exact URLs, official docs, or error snippets | `perplexity_search` | Fastest; returns ranked web snippets you synthesize directly. Default choice for simple lookups. |
| Single pre-synthesized answer with numbered citations across multiple pages | `perplexity_ask` | Fast to moderate; use instead of `perplexity_search`, not after it. |
| Multi-step analysis, architecture tradeoffs, or technical comparisons | `perplexity_reason` | Moderate; step-by-step web-grounded reasoning with citations. |
| Comprehensive multi-source report on a broad topic | `perplexity_research` | Slow (can take several minutes); use only when the user asks for deep research. |

## Search Best Practices

1. For simple factual lookups, make one `perplexity_search` call with a short, natural query (2 to 6 words), `search_type: "fast"`, and `max_results: 5` so results stay concise and inline, then answer directly from the returned snippets.
2. Issue separate `perplexity_search` calls only for genuinely distinct sub-questions or entities, not to re-ask the same question with `perplexity_ask`.
3. Filter when the source or time window is known:
   - `search_recency_filter`: `"hour"`, `"day"`, `"week"`, `"month"`, or `"year"`.
   - `search_domain_filter`: allowlist domains (for example `["docs.python.org", "github.com"]`) or exclude domains with a `-` prefix (for example `["-reddit.com"]`). If a strict domain filter returns too few results, retry without it.
   - `country`: ISO 3166-1 alpha-2 code (for example `"US"`, `"GB"`) for regional results.
   - `max_results`: up to `20` (default `10`); `max_tokens_per_page`: `256` to `2048` (default `1024`).
4. On `perplexity_ask`, `perplexity_reason`, and `perplexity_research`, pass `messages` as a conversation array (`[{"role": "user", "content": "..."}]`). Include `search_recency_filter` or `search_domain_filter` when freshness or source authority matters.
5. Preserve source URLs and publication dates in your final answer so the user can verify claims directly.
