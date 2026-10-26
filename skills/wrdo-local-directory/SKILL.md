---
name: wrdo-local-directory
description: Find local businesses in the Western Cape, South Africa, read their prices and hand a person over to WRDO to finish a booking, quote or order. Public, read-only, no API key.
---

# WRDO local directory

WRDO is a South African app for getting things done with local businesses. This skill uses WRDO's public directory to find businesses and prices, then hands the person over to WRDO to finish.

## When to use

- The person wants a local service, a table, food or a price in the Western Cape (for example a plumber in Stellenbosch).
- You need to know what kinds of businesses exist in a place.
- You want a business's hours, WRDO reviews or price list.

Do not use it for places outside South Africa, or to book or pay by yourself: nothing is booked by these tools.

## Call order (MCP)

Server: https://api.wrdo.co.za/mcp (Streamable HTTP, no sign-in)

1. `list_areas` to match a place name such as Stellenbosch.
2. `list_categories` to see what kinds of businesses exist in that place.
3. `search_local_businesses` to filter by category, price list, price and open now.
4. `get_business` for a business's page, hours and WRDO reviews, and `get_price_list` for its prices.
5. `start_request` to get a hand-off link. The person opens it to finish in WRDO.

## Call order (REST)

All on https://api.wrdo.co.za:

1. `GET /v1/areas?query=`
2. `GET /v1/categories?where=`
3. `GET /v1/businesses?what=&where=`
4. `GET /v1/businesses/{id}` and `GET /v1/businesses/{id}/price-list`
5. `POST /v1/requests`

The OpenAPI description is at https://api.wrdo.co.za/openapi.json.

## Limits

- 30 requests a minute per caller. Over the limit you get HTTP 429 with `retryAfter`: wait that long, then try again.
- No API key and no sign-up.
- Results carry no phone numbers or email addresses.

## Nothing is booked

These tools only read the directory. `start_request` returns a link and nothing more: the person opens it and finishes the booking, quote or order in WRDO. Say so plainly, and never tell the person something is booked.

More: https://wrdo.co.za/developers
