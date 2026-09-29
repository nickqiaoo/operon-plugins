# operon-plugins

Plugin marketplace curated for [operon](https://github.com/nickqiaoo). Same layout as
[`openai/plugins`](https://github.com/openai/plugins): the index lives in
`.agents/plugins/marketplace.json` and each plugin is a directory under `plugins/` with a
`.codex-plugin/plugin.json` manifest, a `.mcp.json`, and optional `skills/`.

| Plugin | MCP server | Auth |
|---|---|---|
| Firecrawl | `https://mcp.firecrawl.dev/v2/mcp-oauth` | OAuth (dynamic client registration) |
| Grafana Cloud | `https://mcp.grafana.com/mcp` | OAuth (dynamic client registration) |
| Interactive Brokers | `https://api.ibkr.com/v1/api/mcp-public` | OAuth (dynamic client registration) |

All servers are hosted by their vendors; this repo only holds the manifests, skills and logos.
Firecrawl's skills are copied unchanged from [`firecrawl/skills`](https://github.com/firecrawl/skills)
(`skills/core` + `skills/build`, the same set its own Codex plugin ships; ISC licensed — see
`plugins/firecrawl/LICENSE`). The upstream commit is recorded in the plugin manifest's `upstream` field.
Logos and trademarks belong to their respective owners.

## Adding a plugin

1. Create `plugins/<name>/` with `.codex-plugin/plugin.json`, `.mcp.json`, `assets/logo.png` and any `skills/<skill>/SKILL.md`.
2. Register it in `.agents/plugins/marketplace.json`.
3. Prefer servers that support OAuth dynamic client registration — operon signs in without a pre-registered client.
