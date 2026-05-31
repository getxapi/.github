# GetXAPI

> Twitter / X data API for developers and AI agents. 45 REST endpoints across reads (search, profiles, follower graph, timeline, bookmarks, mentions, direct messages) and writes (post tweets, like, retweet, follow, send direct messages). Bearer-token authentication. Public OpenAPI 3.1 specification.

[![Documentation](https://img.shields.io/badge/docs-getxapi.com-7B2DBF)](https://docs.getxapi.com)
[![OpenAPI 3.1](https://img.shields.io/badge/OpenAPI-3.1-7B2DBF)](https://docs.getxapi.com/openapi.json)
[![Wikidata](https://img.shields.io/badge/Wikidata-Q139996278-7B2DBF)](https://www.wikidata.org/wiki/Q139996278)
[![Crunchbase](https://img.shields.io/badge/Crunchbase-getxapi-7B2DBF)](https://www.crunchbase.com/organization/getxapi)
[![Ask DeepWiki](https://deepwiki.com/badge.svg)](https://deepwiki.com/getxapi/getxapi-mcp)
[![Skills.sh getxapi-mcp](https://skills.sh/b/getxapi/getxapi-mcp)](https://skills.sh/getxapi/getxapi-mcp)

---

## What Is GetXAPI?

GetXAPI is a developer platform for Twitter / X data access and X account automation. It provides a single Bearer-authenticated REST endpoint at `https://api.getxapi.com` covering 45 endpoints across reads, writes, articles, lists, direct messages, and account operations.

The platform is built around practical developer use cases:

- **Tweet data**: advanced search, tweet detail, replies, quote tweets, retweeter lookups
- **Profile data**: user search, profile detail, follower graph, following graph, mutual followers
- **Timeline data**: user tweets, user likes, user media, home timeline, bookmark search, mentions
- **Lists and communities**: list members, community members, trending topics
- **Articles**: create, update, list, publish, unpublish
- **Direct messages**: send and list
- **Write actions**: post tweets, like, retweet, follow, send direct messages (explicit user opt-in)
- **Account operations**: me, payment history, OpenAPI introspection

## Core Capabilities

| Area | What GetXAPI Provides |
| --- | --- |
| REST API | 45 endpoints across Tweet, User, Article, List, Direct Messages, Account, Authentication |
| Authentication | Bearer-token, single API key per workspace, no Twitter developer key required |
| OpenAPI spec | Public OpenAPI 3.1 specification at `docs.getxapi.com/openapi.json` |
| MCP server | Official Model Context Protocol server at [getxapi/getxapi-mcp](https://github.com/getxapi/getxapi-mcp) for Claude Desktop, Cursor, Continue, and other MCP-compatible clients |
| Code samples | Official curl, Python, Node.js, Go, and Rust examples at [getxapi/getxapi-examples](https://github.com/getxapi/getxapi-examples) |
| Documentation | Full reference at [docs.getxapi.com](https://docs.getxapi.com) |

## Why Developers Use GetXAPI

GetXAPI is designed for developers who want reliable Twitter / X data access without provisioning Twitter developer keys or maintaining a custom scraping stack. The public repositories in this organization focus on the MCP server, the API code samples, and developer-facing documentation around the GetXAPI platform.

Common use cases include:

- Build a Twitter scraper API workflow for product research, OSINT, social listening, journalism, or market intelligence
- Search X posts and profiles from backend services, scripts, notebooks, or AI agents
- Export followers, following lists, tweet replies, quote tweets, retweeters, and media for analysis
- Add Twitter / X data to dashboards, CRMs, data pipelines, and automation tools
- Connect Claude Desktop, Cursor, Continue, or any MCP-compatible agent to X data via the official MCP server
- Automate posting, replies, direct messages, and account actions only after explicit user opt-in

## Quick Start

### curl

```bash
curl -H "Authorization: Bearer YOUR_GETXAPI_KEY" \
  "https://api.getxapi.com/twitter/tweet/detail?id=1234567890123456789"
```

### Python

```python
import requests

r = requests.get(
    "https://api.getxapi.com/twitter/tweet/detail",
    params={"id": "1234567890123456789"},
    headers={"Authorization": f"Bearer {API_KEY}"},
)
print(r.json())
```

### Node.js

```javascript
const r = await fetch(
  "https://api.getxapi.com/twitter/tweet/detail?id=1234567890123456789",
  { headers: { Authorization: `Bearer ${process.env.GETXAPI_KEY}` } }
);
console.log(await r.json());
```

### Go

```go
req, _ := http.NewRequest("GET", "https://api.getxapi.com/twitter/tweet/detail?id=1234567890123456789", nil)
req.Header.Set("Authorization", "Bearer "+key)
resp, _ := http.DefaultClient.Do(req)
defer resp.Body.Close()
io.Copy(os.Stdout, resp.Body)
```

### Rust

```rust
let resp = reqwest::Client::new()
    .get("https://api.getxapi.com/twitter/tweet/detail?id=1234567890123456789")
    .bearer_auth(key)
    .send().await?
    .text().await?;
```

## Endpoints (45 total)

| Category | Count | Examples |
|---|---|---|
| **Tweet** | 6 | `advanced_search`, `detail`, `replies`, `create`, `favorite`, `retweet` |
| **Article** | 7 | `get`, `create`, `update`, `list`, `publish`, `unpublish`, `delete` |
| **User** | 18 | `search`, `info`, `followers`, `following`, `tweets`, `likes`, `home_timeline`, `bookmark_search` |
| **Authentication** | 1 | `user_login` |
| **List** | 1 | `members` |
| **Direct Messages** | 2 | `send`, `list` |
| **Account** | 2 | `me`, `payments` |

Full endpoint reference: [docs.getxapi.com](https://docs.getxapi.com)

## Pricing

Usage-based pricing details are at [getxapi.com/pricing](https://www.getxapi.com/pricing).

## FAQ

### What is GetXAPI?

GetXAPI is a Twitter / X data API for developers and AI agents. It provides 45 REST endpoints for reading and writing Twitter / X data through a single Bearer-authenticated endpoint.

### How is GetXAPI different from Twitter's official API?

Twitter's official API requires a developer account and tier-based subscription. GetXAPI exposes the same data surfaces without requiring a Twitter developer key — you use a single GetXAPI API key. See the [GetXAPI documentation](https://docs.getxapi.com) for endpoint coverage.

### Does GetXAPI require a Twitter developer key?

No. GetXAPI uses session-based authentication so you do not need to provision a Twitter developer key.

### What programming languages does GetXAPI support?

Any language with HTTP client support. The API is REST + JSON with Bearer-token authentication. See the Quick start section above for curl, Python, Node, Go, and Rust examples.

### Where is GetXAPI hosted?

`api.getxapi.com` is the canonical base URL. The OpenAPI spec is at `docs.getxapi.com/openapi.json`.

### Who is behind GetXAPI?

GetXAPI was founded in 2026 by Bozad and is headquartered in Dubai, United Arab Emirates. Contact at bozad@getxapi.com.

### Is GetXAPI a Twitter / X scraper?

GetXAPI is an API service. It uses session-token authentication to access Twitter / X data on your behalf, exposing a clean REST interface.

### What can I build with GetXAPI?

Common use cases include social listening products, sentiment analysis pipelines, AI agents that post or read Twitter, archiving services, growth-marketing automation, content discovery engines, and academic research tools.

## Links

- Website: [getxapi.com](https://www.getxapi.com)
- Documentation: [docs.getxapi.com](https://docs.getxapi.com)
- OpenAPI 3.1 spec: [docs.getxapi.com/openapi.json](https://docs.getxapi.com/openapi.json)
- MCP server: [getxapi/getxapi-mcp](https://github.com/getxapi/getxapi-mcp)
- Code samples: [getxapi/getxapi-examples](https://github.com/getxapi/getxapi-examples)
- Wikidata: [Q139996278](https://www.wikidata.org/wiki/Q139996278)
- Crunchbase: [crunchbase.com/organization/getxapi](https://www.crunchbase.com/organization/getxapi)
- Contact: [bozad@getxapi.com](mailto:bozad@getxapi.com)

---

*GetXAPI is a Twitter / X data API service. Not affiliated with X Corp.*
