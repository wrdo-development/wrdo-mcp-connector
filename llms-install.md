# Installing the WRDO MCP server

WRDO is a hosted, remote MCP server. There is nothing to download, build or run, and it needs no API key or sign-in.

- URL: `https://api.wrdo.co.za/mcp`
- Transport: Streamable HTTP
- Authentication: none

Add it to the MCP settings file under the name `wrdo`:

```json
{
  "mcpServers": {
    "wrdo": {
      "type": "streamableHttp",
      "url": "https://api.wrdo.co.za/mcp"
    }
  }
}
```

To check it works, call `search_local_businesses` with `{"what": "pizza", "where": "Stellenbosch"}`. It returns a list of restaurants with an `id` for each, which `get_business` and `get_price_list` take.

Notes:

- Coverage is the Western Cape, South Africa. A search elsewhere returns a short message saying so.
- `start_request` never books or charges anything. It returns a link the person opens to finish in WRDO.
- Right after WRDO deploys, the server can answer "starting up" for a minute or two. Wait and retry.
