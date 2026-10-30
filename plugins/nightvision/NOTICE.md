# Licensing notice

Vendored from <https://github.com/nvsecurity/nightvision-mcp>, directory
`plugins/nightvision/`, at the commit recorded under `_provenance` in
`.corepass-plugin/marketplace.json`.

- The repository carries no top-level `LICENSE` file (GitHub reports
  `license: null`).
- The plugin's own manifests (`.claude-plugin/plugin.json`,
  `.codex-plugin/plugin.json`) and `package.json` declare `MIT`.
- `skills/` is copied by upstream from
  <https://github.com/nvsecurity/nightvision-skills> and keeps that
  repository's Apache-2.0 licence in `skills/LICENSE`.
- `build/core/server.mjs` is upstream's esbuild bundle; the licences of the
  packages bundled into it are listed in `THIRD_PARTY_LICENSES.txt`.

Nothing here is relicensed. If a redistributable licence is not confirmed, the
catalog listing of `nightvision-skills` (skills only, Apache-2.0) is the
fallback.
