# WRDO connector: notes for agents

## What this is

WRDO is a hosted, read-only MCP server for local businesses in the Western Cape, South Africa, including Cape Town and the Winelands. Use it to find businesses, read their menus and price lists, and hand a person a link to start a request in WRDO.

Use it when someone asks for a local business, a menu item, a price, or a service in the Western Cape. Do not use it for places outside the Western Cape.

## Connect

- Address: `https://api.wrdo.co.za/mcp`
- Transport: Streamable HTTP
- No API key and no sign-up.
- Results never carry phone numbers or email addresses.

## Tools

- `list_areas`: the areas WRDO covers. Use it to check a town or suburb name.
- `list_categories`: the types of business listed, with counts for a place.
- `search_local_businesses`: find businesses by service, name, town or suburb. Filter by category, price list, maximum price in rand and open now.
- `get_business`: a public business profile (category, area, hours and address where verified).
- `get_price_list`: a business's menu or prices in rand. Website-sourced prices may be unconfirmed.
- `start_request`: returns a hand-off link with status `not_booked`. Nothing is booked, ordered or paid.

## Call order

1. `list_areas` or `list_categories`
2. `search_local_businesses`
3. `get_business` and `get_price_list`
4. `start_request`

Tell the person the link is only a hand-off. They finish in WRDO.

## Limits

- 30 requests a minute per caller. Over the limit you get HTTP 429 with a `Retry-After` header; wait that long, then retry.
- Prices and hours can change. Suggest the person confirms important details with the business.

## Links

- Developer docs: https://wrdo.co.za/developers
- OpenAPI spec: https://api.wrdo.co.za/openapi.json
- REST twin: https://api.wrdo.co.za/v1/
- Security reports: [SECURITY.md](SECURITY.md)
- Contact: hello@wrdo.co.za
