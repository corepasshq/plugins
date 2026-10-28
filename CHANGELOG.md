# Changelog

## [Unreleased]

- Temporarily exclude the pinned Domino Data Lab plugin until an updated source passes Remy compatibility checks.
- Publish each MCP server's launch facts in its `execution` entry, the program each command hook starts, each plugin's local sign-in hints, and where each plugin can run (`surfaces`, with `cloudUnsupported` reasons for desktop-only plugins).
- Add RingCentral Chat, RingCentral Phone, Rippling and ServiceNow; hold back Windsor.ai, whose MCP server declares an unsupported transport; re-pin 108 upstream plugins.
