# opencode-tavily

OpenCode plugin for [Tavily](https://tavily.com) — gives your AI agent reliable web search, content extraction, crawling, URL discovery, and deep research with citations.

## Installation

Add the plugin to your `opencode.json`:

```json
{
  "$schema": "https://opencode.ai/config.json",
  "plugin": ["opencode-tavily"]
}
```

Then install the Tavily CLI globally:

```bash
curl -fsSL https://cli.tavily.com/install.sh | bash
```

Or via Python:

```bash
uv tool install tavily-cli
# or
pip install tavily-cli
```

## Authentication

On first use, the agent will prompt you to authenticate. You can also set up in advance:

```bash
# Browser login (recommended)
tvly login
# Or set an API key
export TAVILY_API_KEY=tvly-your-api-key
```

Get an API key at [tavily.com](https://tavily.com).

If `TAVILY_API_KEY` is set in your environment, the plugin automatically passes it to shell commands.

## What It Does

This plugin registers the Tavily CLI skill with OpenCode. Once installed, the agent can:

- **Search** the web with optional content extraction
- **Scrape / Extract** any webpage to clean markdown, HTML, or structured data
- **Map** all URLs on a website
- **Crawl** entire websites recursively
- **Research** — AI-powered deep research with citations

All output is written to a `.tavily/` directory to avoid flooding context.

## Tools Summary

| Command | Use When | Key Flags |
|---------|----------|-----------|
| `tvly search` | No specific URL yet — find sources and answer questions | `--search-depth`, `--max-results`, `--time-range` |
| `tvly extract` | Have a URL — pull clean content | `--extract-depth`, `--query`, `--chunks-per-source` |
| `tvly map` | Need to discover URLs on a large site | `--limit`, `--search` |
| `tvly crawl` | Need bulk content from a site section | `--max-depth`, `--max-breadth`, `--output-dir` |
| `tvly research` | Need comprehensive, multi-source analysis | `--model`, `--stream` |

## Links

- [Tavily](https://tavily.com)
- [Tavily Documentation](https://docs.tavily.com)
- [Tavily CLI Installation](https://cli.tavily.com)
- [OpenCode Plugin Docs](https://opencode.ai/docs/plugins)
- [OpenCode Ecosystem](https://opencode.ai/docs/ecosystem)

## License

MIT
