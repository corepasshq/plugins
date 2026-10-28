# Changelog

## [Unreleased]

- Temporarily exclude the pinned Domino Data Lab plugin until an updated source passes Remy compatibility checks.
- Publish each MCP server's launch facts in its `execution` entry, the program each command hook starts, each plugin's local sign-in hints, and where each plugin can run (`surfaces`, with `cloudUnsupported` reasons for desktop-only plugins).
- Add RingCentral Chat, RingCentral Phone, Rippling and ServiceNow; hold back Windsor.ai, whose MCP server declares an unsupported transport; re-pin 108 upstream plugins.
- Circleback, Clay, Hunter, Intercom, Playwright and Vanta, which both the Claude Code and Cursor marketplaces list, are published once each from the vendor's own Claude Code listing (Playwright from Anthropic's) by a reviewed decision in corepasshq/remy `scripts/catalog/catalog_duplicates.json`; a name both marketplaces list with no decision now stops the regeneration. The published entries are unchanged.
