---
name: perplexity-search
description: Use Perplexity for AI-powered web search via MCP to get real-time information. Use this skill when you need to perform web searches for current information, find the latest scientific literature, get reliable answers with source citations, or access information beyond the model's knowledge cutoff. Provides both search (quick search) and research (deep research) modes.
---

# Perplexity Search

AI-powered web search using Perplexity via MCP. Prioritize using the `pro` mode for high-quality results.

## Quick Start

### Quick Search (Free)
```yaml
search:
  query: "weather today"
  mode: "auto"
```

### Professional Search (Recommended)
```yaml
search:
  query: "latest developments in CRISPR"
  mode: "pro"
  sources: ["web"] # or "scholar", "social"
```

### Deep Research
```yaml
research:
  query: "analysis of AlphaFold3 vs AlphaFold2"
  mode: "reasoning" # or "deep research"
```

## Detailed Guide

For a comprehensive guide on search strategies, tool selection (search vs. research), and advanced configuration options, please refer to [search-strategy.md](references/search-strategy.md).

It covers:
- When to use `search` vs `research`
- Detailed breakdown of modes (`auto`, `pro`, `reasoning`, `deep research`)
- Source selection (`web`, `scholar`, `social`)
- Decision tree for tool selection
