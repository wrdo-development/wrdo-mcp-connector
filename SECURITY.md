# Security

This repository holds configuration only. The WRDO MCP server it points to, `https://api.wrdo.co.za/mcp`, is hosted and run by WRDO.

## Reporting a problem

Email **hello@wrdo.co.za** with the subject line `Security`. Please include:

- what you found and where (URL, tool name, request)
- the steps to reproduce it
- what an attacker could do with it

We reply within 3 working days. Please don't open a public issue for a security problem, and don't test against other people's data.

## Scope

- `https://api.wrdo.co.za/mcp` (the public MCP server)
- `https://api.wrdo.co.za/.well-known/agent-card.json` and `https://api.wrdo.co.za/a2a` (A2A)
- the files in this repository
