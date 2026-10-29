# Changelog

## [Unreleased]

- List each plugin's skills, commands, agents and rules as Remy loads them, under the names users invoke (19 plugins change: cockroachdb, mattpocock-skills, mlflow, planetscale and twilio-developer-kit gain skills; amd-skills, supabase, vercel and coderabbit drop folders and files Remy does not load; notion and posthog commands are namespaced; outputai, sonarqube, stripe and zapier agents take their frontmatter names; cloudflare, grafana-assistant, zapier, zscaler and four Cursor plugins gain `.mdc` and declared rules). A renamed skill keeps its written name as `upstreamName` (pinecone's `pinecone:assistant` is `assistant`; zscaler's `application_segment` skills are slugged). An MCP server its author disabled is marked `disabled` (databases-on-aws).
- Each hook group carries `entries`, one per hook with its portable toggle key, event, matcher, content hash and occurrence (190 entries over 55 plugins, 7 in the Cursor feed).
- Each probed remote MCP server's `execution` entry carries `oauthSignIn: {signIn, verdict}` from the remote sign-in check, and the feed carries `oauthPolicy.domainGroups`, the reviewed vendor domain groups remy-service signs in with. `execution[].oauth` stays the generator's boolean (the server config has an oauth block) on every remote entry.
- Publish Slack from the vendored track; re-pin 69 upstream plugins.
- Publish Questrade and OnePay after review (standard OAuth 2.1 remote MCP servers that sign in by address); keep Business Central out as Cursor-only (it ships no MCP server).

- Publish Slack from the vendored `plugins/slack` again. Its MCP config no longer carries a client id: Remy signs in through remy-service with the Slack app Remy's Slack agent uses.
- Temporarily exclude the pinned Domino Data Lab plugin until an updated source passes Remy compatibility checks.
- Publish each MCP server's launch facts in its `execution` entry, the program each command hook starts, each plugin's local sign-in hints, and where each plugin can run (`surfaces`, with `cloudUnsupported` reasons for desktop-only plugins).
- Add RingCentral Chat, RingCentral Phone, Rippling and ServiceNow; hold back Windsor.ai, whose MCP server declares an unsupported transport; re-pin 108 upstream plugins.
- Circleback, Clay, Hunter, Intercom, Playwright and Vanta, which both the Claude Code and Cursor marketplaces list, are published once each from the vendor's own Claude Code listing (Playwright from Anthropic's) by a reviewed decision in corepasshq/remy `scripts/catalog/catalog_duplicates.json`; a name both marketplaces list with no decision now stops the regeneration. The published entries are unchanged.
