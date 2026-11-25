# Perplexity API Tools

When a task depends on live web information, current documentation, recent releases, error lookups, or verified citations outside the local workspace, pick the single best Perplexity API MCP tool and stop once the result answers the question:

- `perplexity_search` (default for quick lookups): live facts, weather, prices, official documentation URLs, changelogs, and error snippets. Answer directly from the snippets; do not follow up with `perplexity_ask` for the same query.
- `perplexity_ask`: single pre-synthesized answer with numbered citations across multiple sources (use instead of `perplexity_search`, not after it).
- `perplexity_reason`: step-by-step technical comparisons and tradeoff analysis grounded in web sources.
- `perplexity_research`: broad, in-depth multi-source reports only (can take several minutes).
