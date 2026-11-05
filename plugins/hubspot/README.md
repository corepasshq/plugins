# HubSpot

Connects agents to [HubSpot](https://www.hubspot.com) through HubSpot's
official remote [Model Context Protocol](https://modelcontextprotocol.io/)
server.

Search and update CRM records, work with activities and conversations, and
manage marketing email drafts in the signed-in HubSpot account.

This is HubSpot's remote CRM MCP server — not the
[developer MCP server](https://developers.hubspot.com/docs/developer-tooling/local-development/developer-mcp/setup),
which helps build apps and CMS assets locally.

## MCP

```json
{
  "mcpServers": {
    "hubspot": {
      "type": "http",
      "url": "https://mcp.hubspot.com"
    }
  }
}
```

## Sign-in

The config carries no client id. Remy signs in to `mcp.hubspot.com` with
Remy's own HubSpot app, held by Remy's sign-in service; each person completes
their own HubSpot OAuth login, so tool calls run with that person's HubSpot
permissions. There is nothing to configure.

## Notes

- If the HubSpot account has Sensitive Data turned on, activity objects and
  conversation data are blocked through the MCP server (this does not affect
  the standard CRM APIs).
- Help desk conversations are visible to all users; conversations-inbox access
  follows the same team/user restrictions as in HubSpot.

## Source

Vendored from [cursor/plugins](https://github.com/cursor/plugins)
`third_party/hubspot` at `c742dd61706fbacc1b95f1a20b7b988cf096ce6c` (MIT). The
upstream config's `CLIENT_ID` / `CLIENT_SECRET` settings and its `auth` block
are removed.

Logo is HubSpot's official inverted favicon (white sprocket on the brand
orange tile) from
https://www.hubspot.com/hubfs/HubSpot_Logos/HubSpot-Inversed-Favicon.png.

## License

MIT
