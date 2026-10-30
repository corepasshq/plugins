# Carta

The Carta MCP server, as a connector the three Carta skill plugins
(`carta-cap-table`, `carta-investors`, `carta-crm`) work through.

- Endpoint: `https://mcp.app.carta.com/mcp` (Streamable HTTP)
- Skill plugins: <https://github.com/carta/plugins> (Apache-2.0), listed in the
  catalog from upstream unchanged

## What this plugin is

One MCP server, nothing else — no skills, commands, agents or hooks. Like
`neon` and `sentry`, the manifest and `.mcp.json` are authored here and the
marketplace entry carries no `_provenance`.

## Why it is separate from the skill plugins

None of Carta's three plugins ships an MCP configuration. Carta's own install
instructions add the server first and the skills second
(`claude mcp add --transport http carta https://mcp.app.carta.com/mcp`, then
`claude plugin install carta-investors`), and in Claude's apps the server comes
from the Carta connector. Installed from the catalog alone, the skills had
nothing to call in Remy.

The server is not added to vendored copies of the skill plugins because each of
those ships its hooks as native binaries for five platforms (about 12 MB per
plugin) and releases often; a copy would be some 55 MB to keep in sync. The
skill plugins find this server as it is: their hooks match any tool whose name
contains `carta`, which `mcp__carta__carta__*` does, and their skills call the
tools by bare name (`crm_call_tool`, `execute_query`, …). Their `allowed-tools`
lists name Claude's server ids, but a skill that runs inline does not apply
them as a tool allowlist.

One server serves all three: the registration below was granted
`read_mcp_firms`, `read_mcp_companies` and `read_mcp_crm` scopes (with their
`readwrite_` pairs) under one client.

## Authentication

Browser-based OAuth at connect time, with no credential to configure. Checked
2026-10-30:

1. `initialize` answers `401` with
   `WWW-Authenticate: Bearer scope="openid cuid", resource_metadata="https://mcp.app.carta.com/.well-known/oauth-protected-resource/mcp"`.
2. `scripts/catalog/check_mcp_oauth.py` in corepasshq/remy judges it
   signable by address (Client ID Metadata Document with `iss`, plus a
   registration endpoint).
3. A public PKCE registration with a loopback redirect returned `201` and a
   `client_id`. Cloudflare refuses Python's default `urllib` user agent on
   `/register` (error 1010); `curl`, `httpx` and a Java client are accepted.

Access is per Carta account: a person sees only the firms and companies their
Carta login can already see.
