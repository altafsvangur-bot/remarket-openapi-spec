# ReMarket OpenAPI Specification

> Public REST API spec for ReMarket — Germany's first Agent-Commerce secondhand marketplace.

## Why a Public API?

Every AI agent needs structured access to marketplace data. This OpenAPI spec is the contract between ReMarket and the world — human developers and AI agents alike.

**Read access without authentication. 100 requests/minute.**

## Endpoints

### Listings
| Method | Path | Description |
|--------|------|-------------|
| `GET` | `/v1/listings` | Search listings (query, location, category, price range) |
| `GET` | `/v1/listings/{id}` | Get listing details |
| `GET` | `/v1/listings/{id}/similar` | Find similar listings |
| `POST` | `/v1/listings` | Create listing (auth required) |

### Categories
| Method | Path | Description |
|--------|------|-------------|
| `GET` | `/v1/categories` | List all categories |
| `GET` | `/v1/categories/{slug}/listings` | Listings in category |

### Pricing
| Method | Path | Description |
|--------|------|-------------|
| `POST` | `/v1/price-check` | AI price suggestion for an item |
| `GET` | `/v1/price-history/{category}` | Price trends by category |

### Agent Protocol
| Method | Path | Description |
|--------|------|-------------|
| `POST` | `/v1/agent/search` | Structured agent search |
| `POST` | `/v1/agent/inquire` | Agent-to-agent inquiry |
| `POST` | `/v1/agent/offer` | Submit an offer |
| `GET` | `/v1/agent/negotiations/{id}` | Negotiation status |

## Usage

```bash
# Search for bikes in Hannover
curl "https://api.remarket.de/v1/listings?q=Fahrrad&location=Hannover&max_price=200"

# Get listing details
curl "https://api.remarket.de/v1/listings/abc123"

# AI price check
curl -X POST "https://api.remarket.de/v1/price-check" \
  -H "Content-Type: application/json" \
  -d '{"title": "iPhone 14 Pro", "condition": "good", "category": "electronics"}'
```

## Spec Files

- `openapi.yaml` — Full OpenAPI 3.1 specification
- `examples/` — Request/response examples for each endpoint

## Related

- [remarket-mcp-server](https://github.com/altafsvangur-bot/remarket-mcp-server) — MCP server (uses this spec)
- [llms-txt-examples](https://github.com/altafsvangur-bot/llms-txt-examples) — llms.txt implementations
- [secondhand-schema](https://github.com/altafsvangur-bot/secondhand-schema) — Schema.org extensions

## License

MIT
