# Perplexity API Plugin for Google Antigravity

Connect Google Antigravity to Perplexity's hosted MCP server (`https://api.perplexity.ai/mcp`) for real-time web search, cited answers, step-by-step reasoning, and deep research.

## What's Included

- **Hosted MCP server (`perplexity`)** with four read-only tools backed by the Perplexity Search API and Agent API:
  - `perplexity_search`: Ranked web search results with titles, URLs, snippets, and dates, plus recency, domain, country, and low-latency (`search_type: "fast"`) controls.
  - `perplexity_ask`: Quick web-grounded answers with numbered citations.
  - `perplexity_reason`: Step-by-step analysis and tradeoff comparisons grounded in web sources.
  - `perplexity_research`: Deep multi-source research reports with numbered citations (may take several minutes).
- **Skill (`/perplexity-search`)**: Guides tool selection across search, ask, reason, and research, plus recency and domain filters.
- **Rule (`rules/AGENTS.md`)**: Always-on guidance for reaching for Perplexity tools when tasks need live web info or citations.

## Setup

Install from the Antigravity Plugin Marketplace, or via the Antigravity CLI:

```bash
agy plugin install https://github.com/perplexityai/antigravity-plugin
```

Then authenticate:

1. Open the plugin's **Accounts** tab in Antigravity and click **Sign in**.
2. Sign in with a Perplexity account that is an admin of a [Perplexity API organization](https://console.perplexity.ai) and select the organization to bill tool usage to.

The OAuth connection is read-only and cannot create API keys or change organization settings.

## Links

- [Antigravity Integration Docs](https://docs.perplexity.ai/docs/getting-started/integrations/antigravity)
- [Perplexity MCP Server Docs](https://docs.perplexity.ai/docs/getting-started/integrations/mcp-server)
- [Perplexity API Console](https://console.perplexity.ai)
- [Support](https://www.perplexity.ai/help-center/en) (`api@perplexity.ai`)
- [Terms of Service](https://www.perplexity.ai/hub/legal/perplexity-api-terms-of-service)
- [Privacy Notice](https://www.perplexity.ai/hub/legal/privacy-notice)
