# GrackerAI MCP Server

Bring your AI visibility data into Claude, ChatGPT, Cursor, and any other MCP client.

[GrackerAI](https://gracker.ai) tracks how AI engines (ChatGPT, Perplexity, Gemini, Copilot, Grok, and Google AI Overviews) talk about your brand. With this MCP server, your AI assistant can query that data live. You don't need to export reports or copy numbers into a chat.

This is a **hosted (remote) MCP server**. There is nothing to install or run. Add the URL below to your client and sign in with your GrackerAI account.

```
https://portal.gracker.ai/mcp
```

- **Transport:** Streamable HTTP
- **Auth:** OAuth (sign in with your GrackerAI account)
- **Access:** Read-only. It cannot change anything in your account.
- **Docs:** https://gracker.ai/docs/advanced/mcp/
- **Product page:** https://gracker.ai/platform/ai-visibility/mcp/

## Setup

### Chat apps

| Client | Where to add it |
|---|---|
| Claude | Settings → Connectors → Add custom connector → paste the URL |
| ChatGPT | Settings → Connectors → Add custom connector → paste the URL |
| Copilot | Settings → Connectors → Add custom connector → paste the URL |
| Gemini | Extensions → Add custom MCP server → paste the URL |
| Grok | Connectors → Add custom connector → paste the URL |
| Perplexity | Settings → Connectors → Add custom connector → paste the URL |

### Cursor

`.cursor/mcp.json`:

```json
{
  "mcpServers": {
    "gracker": {
      "url": "https://portal.gracker.ai/mcp"
    }
  }
}
```

### VS Code

`.vscode/mcp.json`:

```json
{
  "servers": {
    "gracker": {
      "type": "http",
      "url": "https://portal.gracker.ai/mcp"
    }
  }
}
```

### Claude Code

```bash
claude mcp add --transport http gracker https://portal.gracker.ai/mcp
```

Any other MCP client works the same way: add the URL in its server settings.

### First connection

A browser window opens so you can log in to GrackerAI. Next, pick which brands this connection can access. All brands start selected, and your assistant only sees the brands you leave selected. To disconnect, remove the connector from your AI client.

## Tools

| Tool | What it does |
|---|---|
| `get_visibility_schema` | Returns the shape of your AI visibility data (types and fields). Your assistant reads this first. |
| `query_visibility_data` | Runs a read-only query against your data. Results are always limited to the brands you authorized. |

## What you can ask

You don't need to learn a query language. Ask in plain words and your assistant writes the query.

- "What's my visibility score for the last 7 days? Break it down by engine."
- "Which tracked prompts had zero mentions of my brand in the last 60 days?"
- "Show negative mentions of my brand this month, with the engine and the prompt that triggered each."
- "Which competitors show up most often in answers where I'm missing?"
- "Which domains do AI answers cite most for my category prompts?"

## Data covered

- **Visibility:** score, presence, and mention counts by prompt, engine, country, and date range
- **Mentions:** each time a brand is named, with position, prominence, sentiment, and whether the claim was accurate
- **Citations:** each URL an AI answer cited, with domain, source type, publish date, and whether it supported the claim
- **Competitors:** the competitors you track plus brands AI engines compare you with
- **Prompts:** your tracked prompts and their results, with intent and funnel stage

## Requirements

You need a GrackerAI account with at least one brand set up. [Start here](https://gracker.ai).

## Support

Questions or problems: open an issue in this repo or see the [docs](https://gracker.ai/docs/advanced/mcp/).
