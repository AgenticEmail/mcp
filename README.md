<p align="center">
  <img src="https://raw.githubusercontent.com/AgenticEmail/.github/main/profile/logo.svg" width="80" alt="AgenticEmail logo">
</p>

<h1 align="center">AgenticEmail MCP Server</h1>

<p align="center"><b>Hosted email for AI agents over the Model Context Protocol</b></p>

<p align="center">
  <a href="https://agenticemail.dev">Website</a> ·
  <a href="https://agenticemail.dev/docs/mcp">Docs</a> ·
  <a href="https://registry.modelcontextprotocol.io">MCP Registry: dev.agenticemail/mcp</a> ·
  <a href="https://discord.gg/ehGyEgrNCb">Discord</a>
</p>

---

AgenticEmail ships a hosted [MCP](https://modelcontextprotocol.io) server so any MCP-compatible agent (Claude, Cursor, Codex, custom agents) can create inboxes and send, receive, and reply to real email as native tool calls - no custom glue code.

The server is remote (streamable HTTP). There is nothing to install or run locally.

## Connect

```json
{
  "mcpServers": {
    "agenticemail": {
      "url": "https://api.agenticemail.dev/mcp",
      "headers": {
        "Authorization": "Bearer ${AGENTICEMAIL_API_KEY}"
      }
    }
  }
}
```

Get an API key at [agenticemail.dev](https://agenticemail.dev) - free while you build. Scoped keys work here too, so an agent only sees the inboxes you grant it.

## Tools

| Tool | Description |
|---|---|
| `create_inbox` | Provision a new addressable inbox |
| `list_inboxes` | List inboxes the key can access |
| `list_threads` / `get_thread` | Browse conversations and load full thread history |
| `list_messages` / `get_message` | Read parsed inbound and outbound messages |
| `send_message` | Send a message from an inbox |
| `reply_to_message` | Reply within an existing thread |

## Example

> Create an inbox for the onboarding flow, send a welcome email to new@example.com, then watch for their reply.

The agent calls `create_inbox`, then `send_message`, and reacts to the reply through your webhook or WebSocket stream.

## Beyond MCP

The same platform is available as a [REST API](https://agenticemail.dev/docs), with webhooks, real-time events, custom domains, SMTP compatibility, and official [TypeScript](https://github.com/AgenticEmail/agenticemail-typescript) and [Python](https://github.com/AgenticEmail/agenticemail-python) SDKs.
