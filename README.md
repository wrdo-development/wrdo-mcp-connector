<p align="center">
  <img src="assets/wrdo-icon.png" alt="WRDO" width="96" height="96">
</p>

<h1 align="center">WRDO for AI assistants</h1>

<p align="center">
  Find local businesses, menus and price lists in the Western Cape, South Africa,<br>
  and start a request with them in WRDO, from any AI assistant that speaks MCP.
</p>

<p align="center">
  <a href="https://wrdo.co.za/support/mcp">Documentation</a> ·
  <a href="https://wrdo.co.za/privacy">Privacy</a> ·
  <a href="https://wrdo.co.za/terms">Terms</a> ·
  <a href="mailto:hello@wrdo.co.za">Support</a>
</p>

---

WRDO is a hosted [Model Context Protocol](https://modelcontextprotocol.io) server. There is nothing to install or run: point your assistant at the URL below.

```
https://api.wrdo.co.za/mcp
```

- **Transport:** Streamable HTTP
- **Sign-in:** none. Every tool is read-only and anonymous.
- **Coverage:** the Western Cape, starting with Paarl and the Cape Winelands.
- **Rate limit:** 30 requests per minute per caller.

This repository holds no server code. It holds the small config files that let Claude Code, Cursor, Gemini CLI and other tools add WRDO in one step.

## What you can ask

> Find an electrician in Paarl.
>
> What's on the menu at Breezy's, and how much is the garlic and cheese pita?
>
> Find a hairdresser in Wellington and start a request for Saturday morning.

## Tools

| Tool | What it does |
|---|---|
| `search_local_businesses` | Find businesses by what they do or their name, optionally in a town or suburb. |
| `get_business` | One business's public WRDO page: category, area, whether it is verified, and more for verified businesses. |
| `get_price_list` | A business's menu or price list: items with prices in rand. Prices taken from the business's own website are marked as not yet confirmed. |
| `start_request` | A link the person opens to ask WRDO for a quote, booking or order. Nothing is booked or paid inside the assistant: the person finishes in WRDO, and prices are only confirmed when the business confirms them. |

Results only ever carry public business information. No phone numbers, email addresses or personal data are returned.

## Add WRDO to your assistant

### Claude (claude.ai and Claude Desktop)

1. Open **Settings → Connectors → Add custom connector**.
2. Name it `WRDO` and paste `https://api.wrdo.co.za/mcp` as the URL.
3. Leave authentication empty and click **Add**.

### Claude Code

```bash
claude mcp add --transport http wrdo https://api.wrdo.co.za/mcp
```

Or install it as a plugin:

```
/plugin marketplace add wrdo-development/wrdo-mcp-connector
/plugin install wrdo@wrdo
```

### Cursor

[Add WRDO to Cursor](https://cursor.com/install-mcp?name=wrdo&config=eyJ1cmwiOiJodHRwczovL2FwaS53cmRvLmNvLnphL21jcCJ9), or add this to `~/.cursor/mcp.json`:

```json
{
  "mcpServers": {
    "wrdo": { "url": "https://api.wrdo.co.za/mcp" }
  }
}
```

### VS Code

[Add WRDO to VS Code](https://insiders.vscode.dev/redirect/mcp/install?name=wrdo&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A//api.wrdo.co.za/mcp%22%7D), or run:

```bash
code --add-mcp '{"name":"wrdo","type":"http","url":"https://api.wrdo.co.za/mcp"}'
```

### Gemini CLI

```bash
gemini extensions install https://github.com/wrdo-development/wrdo-mcp-connector
```

### Goose

Run `goose configure`, choose **Add Extension**, pick the remote Streamable HTTP option, name it `wrdo` and paste `https://api.wrdo.co.za/mcp`.

### Any other client

Most clients take the URL directly. A client that only runs local (stdio) servers can bridge to it:

```bash
npx -y mcp-remote https://api.wrdo.co.za/mcp
```

## Agent-to-agent (A2A)

WRDO also publishes a signed A2A agent card:

```
https://api.wrdo.co.za/.well-known/agent-card.json
```

## Listed in

- [Official MCP Registry](https://registry.modelcontextprotocol.io) as `za.co.wrdo/wrdo`
- [Glama](https://glama.ai/mcp/connectors/za.co.wrdo/wrdo)

## Support

- Documentation: <https://wrdo.co.za/support/mcp>
- Email: <hello@wrdo.co.za>
- Issues with these config files: [open an issue](https://github.com/wrdo-development/wrdo-mcp-connector/issues)

To report a security problem, see [SECURITY.md](SECURITY.md).

## License

The config files in this repository are [MIT licensed](LICENSE). The WRDO name and logo are trademarks of WRDO and are not covered by the license.
