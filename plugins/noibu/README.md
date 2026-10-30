# Noibu

Noibu's ecommerce analytics skills, with the Noibu MCP server they drive.

- Upstream: <https://github.com/Noibu/ai-plugin> (`src/`, MIT)
- Endpoint: `https://mcp.noibu.com/mcp` (Streamable HTTP)

## Why this copy exists

Upstream ships only skills. Its manifest says "Connects Claude to the Noibu MCP
server", but the plugin carries no MCP configuration: Claude users connect Noibu
as a separate connector, and every skill stops when it is missing
(`tech-diagnosis`: "Noibu MCP — confirm connected. If not, stop."). Installed
as-is from the catalog, the skills had nothing to call in Remy.

This copy adds the one file upstream leaves out, `.mcp.json`. The skills,
upstream's `.claude-plugin/plugin.json` and `LICENSE` are copied unchanged from
the commit recorded under `_provenance` in `.corepass-plugin/marketplace.json`.

## Authentication

Browser-based OAuth at connect time, with no credential to configure. The
server publishes protected-resource metadata and an RFC 7591 registration
endpoint; checked 2026-10-30:

1. `initialize` answers `401` with
   `WWW-Authenticate: Bearer … resource_metadata="https://mcp.noibu.com/.well-known/oauth-protected-resource"`.
2. `scripts/catalog/check_mcp_oauth.py` in corepasshq/remy judges it
   signable by address (Client ID Metadata Document with `iss`, plus a
   registration endpoint).
3. A public PKCE registration with a loopback redirect returned `201` and a
   `client_id`.

## Known gaps

Some skills reach for tools only Claude's own apps provide: `tech-diagnosis`
and the analysis skills render with `mcp__visualize__show_widget`, and one
setup step asks the user to disconnect Claude's GitHub connector. In Remy those
steps fall back to plain answers; the Noibu data tools are unaffected.
