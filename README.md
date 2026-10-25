 <p align="center">
  <img src="assets/wrdo-icon.png" alt="WRDO logo" width="96" height="96">
</p>

<h1 align="center">WRDO for AI Assistants</h1>

<p align="center">
  Discover local businesses, menus and price lists across the Western Cape, South Africa.<br>
  Find businesses and start quote, booking or order requests through WRDO, using compatible AI assistants.<br>
  <strong><a href="https://wrdo.co.za">WRDO — World Ready Digital Operator</a></strong>
</p>

<p align="center">
  <a href="https://wrdo.co.za/support/mcp">Documentation</a> ·
  <a href="https://wrdo.co.za">Website</a> ·
  <a href="https://wrdo.co.za/privacy">Privacy</a> ·
  <a href="https://wrdo.co.za/terms">Terms</a> ·
  <a href="mailto:hello@wrdo.co.za">Support</a>
</p>

<p align="center">
  <a href="https://cursor.com/install-mcp?name=wrdo&config=eyJ1cmwiOiJodHRwczovL2FwaS53cmRvLmNvLnphL21jcCJ9"><img src="https://cursor.com/deeplink/mcp-install-dark.svg" alt="Add WRDO to Cursor" height="32"></a>
  <a href="https://insiders.vscode.dev/redirect/mcp/install?name=wrdo&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A//api.wrdo.co.za/mcp%22%7D"><img src="https://img.shields.io/badge/Add%20to%20VS%20Code-0098FF?style=for-the-badge&logo=visualstudiocode&logoColor=white" alt="Add WRDO to VS Code" height="32"></a>
</p>

<p align="center">
  <a href="https://protocolprobe.com/mcp/servers/za.co.wrdo/wrdo"><img src="https://protocolprobe.com/api/v1/badge/za.co.wrdo/wrdo" alt="ProtocolProbe record checks for WRDO"></a>
  <a href="https://aiagentslisting.com/mcp/wrdo-mcp-connector"><img src="https://aiagentslisting.com/wrdo-mcp-connector/badge.svg?claim=99f55a9a2d19a68a13d264d3fca048bc" alt="WRDO MCP Connector on AI Agents Listing"></a>
</p>

---

## What is WRDO?

WRDO stands for **World Ready Digital Operator**. It connects AI assistants to local business information in the Western Cape, South Africa, through the [Model Context Protocol (MCP)](https://modelcontextprotocol.io).

With WRDO, compatible AI assistants can discover local businesses, browse public business profiles, retrieve menus and price lists, and generate links that let people start quote, booking or order requests through WRDO.

**Website:** [https://wrdo.co.za](https://wrdo.co.za)  
**MCP endpoint:** `https://api.wrdo.co.za/mcp`  
**Documentation:** [https://wrdo.co.za/support/mcp](https://wrdo.co.za/support/mcp)

WRDO is a hosted remote MCP server. You do not need to host the server yourself or run a local copy.

### Connection details

- **Transport:** Streamable HTTP
- **Endpoint:** `https://api.wrdo.co.za/mcp`
- **Authentication:** No authentication is currently required to connect.
- **Coverage:** The Western Cape, South Africa, including Cape Town, Paarl and the Cape Winelands.
- **Rate limit:** 30 requests per minute per caller.

This repository contains configuration and integration files, not the hosted server's implementation.

## What can you do with WRDO?

Ask your AI assistant in ordinary language.

**Find a local business**
```text
Find a hairdresser in Cape Town.
```

**Explore restaurants and prices**
```text
Which restaurants in Paarl have a menu item under R100?
```

**Look up a menu item**
```text
What's on the menu at Breezy's, and how much is the garlic and cheese pita?
```

**Start a request**
```text
Find a hairdresser in Wellington and help me start a request for Saturday morning.
```

Your assistant can select the appropriate WRDO tool based on your request.

## Available tools

WRDO exposes five MCP tools.

| Tool | Description |
|---|---|
| `search_local_businesses` | Search by service, business name, town or suburb. Results can be filtered by category, whether a price list is available, maximum price in rand and whether the business is open now. |
| `list_categories` | Browse the types of businesses listed on WRDO, including category counts for a location or the wider directory. |
| `get_business` | Retrieve a public business profile, including its category, area and verification status. Verified profiles may include a description, address, opening hours, website and menu link. |
| `get_price_list` | Retrieve a business's menu or price list, including item names, descriptions and prices in South African rand. Website-sourced prices may be unconfirmed. |
| `start_request` | Generate a link for a person to start a quote, booking or order request through WRDO. The person continues the process in WRDO. |

### Important limitations

- Business information and prices may change. Confirm important details with the business.
- Website-sourced prices may not have been confirmed by the business.
- A request link is not a confirmed booking, order or quote.
- The MCP server does not itself complete bookings or process payments.
- The connector returns public business information made available through WRDO. Its tools do not return business phone numbers, email addresses or personal data.

## Installation

For the latest setup instructions and compatibility information, see the [WRDO MCP documentation](https://wrdo.co.za/support/mcp).

### Claude Desktop and claude.ai

1. Open Claude settings and find the connectors section.
2. Choose the option to add a custom connector, if available on your plan.
3. Name it `WRDO`.
4. Enter the remote MCP endpoint:

   `https://api.wrdo.co.za/mcp`

5. Complete the connection flow provided by your client.

Available options may vary between Claude products and account types.

### Claude Code

Add WRDO as a remote HTTP MCP server:

```bash
claude mcp add --transport http wrdo https://api.wrdo.co.za/mcp
```

Alternatively, if using the WRDO plugin marketplace:

```text
/plugin marketplace add wrdo-development/wrdo-mcp-connector
/plugin install wrdo@wrdo
```

### Cursor

Use the [Add WRDO to Cursor](https://cursor.com/install-mcp?name=wrdo&config=eyJ1cmwiOiJodHRwczovL2FwaS53cmRvLmNvLnphL21jcCJ9) link, or add the following to `~/.cursor/mcp.json`:

```json
{
  "mcpServers": {
    "wrdo": {
      "url": "https://api.wrdo.co.za/mcp"
    }
  }
}
```

### Visual Studio Code

Use the [Add WRDO to VS Code](https://insiders.vscode.dev/redirect/mcp/install?name=wrdo&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A//api.wrdo.co.za/mcp%22%7D) link.

Alternatively, use your version of VS Code's MCP configuration interface to add a remote server with the URL:

`https://api.wrdo.co.za/mcp`

### Gemini CLI

Install the WRDO extension from GitHub:

```bash
gemini extensions install https://github.com/wrdo-development/wrdo-mcp-connector
```

### Goose

1. Open Goose's extension configuration.
2. Add a remote MCP extension using Streamable HTTP.
3. Name it `wrdo`.
4. Set the endpoint to `https://api.wrdo.co.za/mcp`.
5. Save and connect.

The precise configuration steps may vary by Goose version.

### Other MCP-compatible clients

For clients that support remote MCP servers over Streamable HTTP, use:

```text
https://api.wrdo.co.za/mcp
```

For clients that only support local standard-input/output (stdio) servers, a bridge such as `mcp-remote` may work:

```bash
npx -y mcp-remote https://api.wrdo.co.za/mcp
```

Client compatibility and configuration requirements vary. Refer to the client's documentation if the connection fails.

## Agent-to-agent (A2A)

WRDO publishes an A2A agent card at:

[https://api.wrdo.co.za/.well-known/agent-card.json](https://api.wrdo.co.za/.well-known/agent-card.json)

Compatible agent-to-agent systems can use this endpoint to discover WRDO's advertised agent information.

## Registries and directories

Find WRDO in the following MCP registries and community directories:

- [Official MCP Registry](https://github.com/mcp/za.co.wrdo/wrdo) — `za.co.wrdo/wrdo`
- [Glama](https://glama.ai/mcp/connectors/za.co.wrdo/wrdo)
- [MCPServers.org](https://mcpservers.org/servers/wrdo-co-za)
- [ProtocolProbe](https://protocolprobe.com/mcp/servers/za.co.wrdo/wrdo)
- [AI Agents Listing](https://aiagentslisting.com/mcp/wrdo-mcp-connector)
- [ClaudeMCP.org](https://www.claudemcp.org/mcp/registry/za-co-wrdo-wrdo-91071d96154a.html)
- [ClaudePluginHub](https://www.claudepluginhub.com/plugins/wrdo-development-wrdo)
- [Feryn.ee](https://feryn.ee/en/showcase/mcp-za-co-wrdo-wrdo)
- [Awesome Remote MCP Servers](https://github.com/punkpeye/awesome-remote-mcp-servers)

### Listing badges

The badges above link to WRDO's ProtocolProbe record and AI Agents Listing profile.

- **ProtocolProbe:** Its badge displays a public-record check count. “5 of 5 record checks met” is not a security rating, security certification or guarantee of safety.
- **AI Agents Listing:** The badge URL includes the claim token supplied for WRDO's listing. Keep that URL intact if you use it to verify or claim the listing.

Directory listings and their status may change independently of this repository.

## Privacy

The WRDO MCP connector provides public business information made available through WRDO. Its tools do not return business phone numbers, email addresses or personal data.

For more information, review:

- [WRDO Privacy Policy](https://wrdo.co.za/privacy)
- [WRDO Terms of Service](https://wrdo.co.za/terms)

## Support and reporting issues

- **Documentation:** [wrdo.co.za/support/mcp](https://wrdo.co.za/support/mcp)
- **Email:** [hello@wrdo.co.za](mailto:hello@wrdo.co.za)
- **Bug reports and feature requests:** [GitHub Issues](https://github.com/wrdo-development/wrdo-mcp-connector/issues)
- **Security reports:** See [`SECURITY.md`](SECURITY.md).

When reporting an issue, include the client you are using, the steps to reproduce it and any relevant error message. Do not share credentials or private information in public issues.

## License and trademarks

The configuration files in this repository are licensed under the [MIT License](LICENSE).

The MIT License applies to the files covered by the repository license. It does not grant rights to WRDO's name or logo, which are not covered by that license.
