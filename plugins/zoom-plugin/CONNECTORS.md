# Connectors

This plugin works in two modes:

- Standalone: Claude uses the bundled Zoom skills and reference material included with this plugin.
- Supercharged: Claude can also use the bundled Zoom MCP servers from [`.mcp.json`](./.mcp.json) for live tool access.

## Included MCP Servers

| Connector | Endpoint | Use For |
|---|---|---|
| `zoom-mcp` | `https://mcp.zoom.us/mcp/zoom/streamable` | Zoom MCP Server workflows for meeting search, cross-Zoom search, recordings, meeting assets, Docs, and Hub content |
| `zoom-meetings-mcp` | `https://mcp.zoom.us/mcp/meeting/streamable` | Meeting-specific search, assets, and recording workflows |
| `zoom-canvas-mcp` | `https://mcp.zoom.us/mcp/canvas/streamable` | Canvas/Docs files, blocks, collaborators, and access workflows |
| `zoom-chat-mcp` | `https://mcp.zoom.us/mcp/chat/streamable` | Chat messages, channels, contacts, files, and sessions |
| `zoom-tasks-mcp` | `https://mcp.zoom.us/mcp/tasks/streamable` | Tasks, steps, comments, assignees, and collaborators |
| `zoom-revenue-accelerator-mcp` | `https://mcp.zoom.us/mcp/revenue_accelerator/streamable` | Revenue Accelerator conversations, deals, analysis, scorecards, CRM, and team workflows |
| `zoom-whiteboard-mcp` | `https://mcp.zoom.us/mcp/whiteboard/streamable` | Whiteboard-specific MCP workflows |

The complete current Zoom server inventory is in
[skills/zoom-mcp/references/servers.md](./skills/zoom-mcp/references/servers.md).

## Legacy Compatibility Paths

The former `/mcp/docs` and `/mcp/team_chat` paths may still respond, but they are not current
entries in Zoom's published MCP server directory. Use Zoom Canvas for new Docs workflows and
Zoom Chat at `/mcp/chat/streamable` for new Chat workflows. Use only the current `mcp.zoom.us`
production host.

## Authentication

In Remy, open the plugin and choose **Connect** on any Zoom server. Remy signs
in with its own Zoom app; one sign-in covers every server listed above, and
Remy renews the token. There are no access tokens to export.

## What You Can Do Without Connectors

- Choose the right Zoom surface for a new integration
- Plan SDK, REST API, webhook, OAuth, and MCP implementations
- Compare Meeting SDK vs Video SDK vs Zoom Apps vs REST API
- Debug architecture, auth, event-delivery, and integration mistakes
- Use the deep Zoom reference library bundled in `skills/`

## What Connectors Add

- Live MCP tool discovery and execution against Zoom-hosted MCP servers
- Real meeting-search, recording-resource, and document workflows
- Whiteboard, Canvas, Chat, Tasks, and Revenue Accelerator tool access when those servers are registered
- Cross-Zoom search through the main `search_zoom` tool when the token has `ai_companion:read:search`

## Notes

- If a command or skill mentions connectors and you are not connected, continue in standalone mode using the reference docs.
- If you are unsure which connector is relevant, start with [`/setup-zoom-mcp`](./skills/setup-zoom-mcp/SKILL.md).
