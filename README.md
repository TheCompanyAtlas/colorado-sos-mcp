# Colorado SOS Business Entity & Registered Agent MCP

Connect your AI assistant to [The Company Atlas](https://thecompanyatlas.com) for Colorado company registry research through the Model Context Protocol.

This listing is a focused entry point for:

- Colorado LLCs, corporations, nonprofits, partnerships, cooperatives and foreign entities from the Secretary of State business database
- Entity status (Good Standing, Delinquent, ...), formation date, principal and mailing addresses
- Registered agents, individuals and commercial agent firms

The MCP connection is provided by The Company Atlas. This repository does not run a separate server.

## Connect

```
https://thecompanyatlas.com/mcp/colorado
```

Add this URL as a custom MCP connector in Claude, Cursor, or any MCP-compatible client. Sign in with Google when prompted.

- Transport: Streamable HTTP
- Auth: Google OAuth (sign in once, stays authorized)
- Docs: [thecompanyatlas.com/tools/colorado-sos](https://thecompanyatlas.com/tools/colorado-sos)

## Tools

### `Colorado_search_companies`

Search entities by name, entity type, status, city, ZIP or formation date. Filters are combined with AND logic; include at least one.

| Parameter | Type | Description |
|---|---|---|
| `q` | string, optional | Entity name substring, 3–120 characters |
| `entityType` | string, optional | Secretary of State entity code, e.g. `DLLC`, `DPC`, `FLLC` |
| `status` | string, optional | Status substring, e.g. `Good Standing` |
| `active` | boolean, optional | Filter by active status |
| `city` | string, optional | Substring of the principal address |
| `zip` | string, optional | 5-digit principal ZIP |
| `formedFrom` / `formedTo` | date, optional | Formation date range |
| `page` / `limit` | integer, optional | Pagination, `limit` up to 50 (default 20) |

### `Colorado_get_company`

Full profile by Colorado ID number (e.g. `20251955891`): registered agent, mailing address, delinquency date, and jurisdiction of formation for foreign entities.

### `Colorado_search_registered_agents`

Find every entity a person or agent firm serves as registered agent for. `name` is a substring of the agent name as filed; `type` narrows to `individual` or `corporate_body`.

## Example prompts

- Find Colorado LLCs in good standing with "brewing" in the name formed in Denver since 2024
- Who is the registered agent for Colorado ID 20251955891?
- How many Colorado entities use C T Corporation System as registered agent?

## Data source

Colorado Secretary of State business database.
