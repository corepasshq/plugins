# NightVision

NightVision's application-security plugin: its MCP server and seven skills
(`api-discovery`, `app-security-scan`, `ci-cd-integration`,
`scan-configuration`, `scan-report`, `scan-triage`, `source-intelligence`).

- Upstream: <https://github.com/nvsecurity/nightvision-mcp>, `plugins/nightvision/`
  (see [NOTICE.md](NOTICE.md) for licensing)
- Replaces the catalog's `nightvision` listing from
  <https://github.com/nvsecurity/nightvision-skills>, which carries the skills
  only

## Why this copy exists

The catalog listed NightVision's skills-only repository. Its
`app-security-scan` skill drives the NightVision MCP server
(`run-app-security-scan`, `wait-for-scan`, …) and had no server to call in
Remy. NightVision now ships the server and the skills together as one plugin in
`nightvision-mcp`; this is that plugin, copied unchanged, plus
`.corepass-plugin/plugin.json`.

Ours declares the server inline with `${CLAUDE_PLUGIN_ROOT}`, as upstream's
`.claude-plugin/plugin.json` does, instead of upstream's `.mcp.json`, whose
`./build/core/server.mjs` relies on a `cwd` of the plugin directory.

## Requirements

The server runs on the person's own machine:

- Node.js 22 or later
- The NightVision CLI 0.18.0 or later on `PATH`, signed in to the person's
  NightVision account (`nightvision login`)

No OAuth and no credential in this plugin: every action runs under the CLI's
own sign-in. Without the CLI the server exits at start ("NightVision CLI not
found at \"nightvision\". Please install NightVision, add it to PATH, or set
NIGHTVISION_CLI_PATH.") and the server shows as failed; the skills that only
run the CLI need it too.

The cloud sandbox has neither the CLI nor a NightVision sign-in, so this plugin
is useful on the desktop only.
