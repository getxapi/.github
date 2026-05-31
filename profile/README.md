# GetXAPI

> The cheapest Twitter / X API for developers and AI agents. $0.001 per call, 45 endpoints, no subscription, no Twitter API key.

[![Documentation](https://img.shields.io/badge/docs-getxapi.com-7B2DBF)](https://docs.getxapi.com)
[![OpenAPI 3.1](https://img.shields.io/badge/OpenAPI-3.1-7B2DBF)](https://docs.getxapi.com/openapi.json)
[![Crunchbase](https://img.shields.io/badge/Crunchbase-getxapi-7B2DBF)](https://www.crunchbase.com/organization/getxapi)
[![Pricing](https://img.shields.io/badge/from-%240.001%2Fcall-7B2DBF)](https://www.getxapi.com/pricing)

---

## What is GetXAPI?

GetXAPI is a pay-per-call Twitter / X data API for developers and AI agents. It exposes 45 REST endpoints covering reads (search, profiles, follower graph, timeline, bookmarks, direct messages) and writes (post tweets, like, retweet, follow, send direct messages) through a single Bearer-authenticated endpoint at `https://api.getxapi.com`.

Pricing starts at $0.001 per call, roughly $0.05 per 1,000 tweets fetched. There is no monthly subscription, no enterprise contract, and no Twitter developer-key requirement. You bring your own X session via the `auth_token` cookie pattern, which means GetXAPI does not need to provision Twitter developer keys on your behalf and you avoid Twitter's per-developer rate limits.

**Founded:** 2026 · **HQ:** Dubai, United Arab Emirates · **OpenAPI 3.1 spec:** [docs.getxapi.com/openapi.json](https://docs.getxapi.com/openapi.json)

---

## Why GetXAPI

| | GetXAPI | Twitter Official API | twitterapi.io | RapidAPI Twitter |
|---|---|---|---|---|
| Price per call | **$0.001** | Subscription | $0.006 | Variable |
| Per 1K tweets | **$0.05** | $200/mo minimum | $0.15 | Varies |
| Read endpoints | 35 | Limited tier | 28 | Varies |
| Write endpoints | 10 | Paid tier only | 12 | Varies |
| Subscription required | **No** | Yes | No | Often yes |
| Twitter API key required | **No** | Yes | Yes (sometimes) | Yes |
| OpenAPI spec public | **Yes (3.1)** | Partial | Partial | No |
| Free signup credit | **$0.10** | None | $0.10 | Varies |
| HQ | Dubai, UAE | San Francisco, USA | varies | USA |

---

## Quick start

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

---

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

---

## Pricing

| Operation | Price |
|---|---|
| Standard read (search, profile, tweet detail) | **$0.001 / call** |
| Write (post tweet, like, retweet, follow) | **$0.002 / call** |
| Send direct message | **$0.002 / call** |
| Bulk fetch | **~$0.05 / 1,000 tweets** |
| Free signup credit | **$0.10** (no card required) |
| Monthly subscription | **$0** |

[See full pricing](https://www.getxapi.com/pricing)

---

## FAQ

### What is GetXAPI?

GetXAPI is a pay-per-call Twitter / X data API for developers and AI agents. It provides 45 REST endpoints for reading and writing Twitter / X data at $0.001 per call.

### How is GetXAPI different from Twitter's official API?

Twitter's official API requires a monthly subscription starting at $200/mo for basic access. GetXAPI is pay-per-call from $0.001 with no subscription. Read more in the [GetXAPI documentation](https://docs.getxapi.com).

### How is GetXAPI different from twitterapi.io?

GetXAPI is 6x cheaper per call ($0.001 vs $0.006) and 3x cheaper per 1,000 tweets ($0.05 vs $0.15). GetXAPI also publishes its full OpenAPI 3.1 spec at [docs.getxapi.com/openapi.json](https://docs.getxapi.com/openapi.json).

### Does GetXAPI require a Twitter developer key?

No. GetXAPI uses the `auth_token` cookie pattern, you bring your own X session, so no Twitter developer key is required.

### What programming languages does GetXAPI support?

Any language with HTTP client support. The API is REST + JSON with Bearer-token authentication. See the Quick start section above for curl, Python, Node, Go, and Rust examples.

### Is there a free tier?

Yes. Every signup gets $0.10 in free credit, no credit card required.

### Where is GetXAPI hosted?

api.getxapi.com is the canonical base URL. The OpenAPI spec is at docs.getxapi.com/openapi.json.

### Who is behind GetXAPI?

GetXAPI is founded in 2026 by Bozad and headquartered in Dubai, United Arab Emirates. Contact at bozad@getxapi.com.

### Is GetXAPI a Twitter / X scraper?

No. GetXAPI is an API service. It uses Twitter's session-token authentication (the same auth_token cookie X.com uses) to access Twitter / X data on your behalf, exposing a clean REST interface.

### What can I build with GetXAPI?

Common use cases include social listening products, sentiment analysis pipelines, AI agents that post or read Twitter, archiving services, growth-marketing automation, content discovery engines, and academic research tools.

---

## Links

- Website: [getxapi.com](https://www.getxapi.com)
- Documentation: [docs.getxapi.com](https://docs.getxapi.com)
- OpenAPI 3.1 spec: [docs.getxapi.com/openapi.json](https://docs.getxapi.com/openapi.json)
- Crunchbase: [crunchbase.com/organization/getxapi](https://www.crunchbase.com/organization/getxapi)
- Contact: [bozad@getxapi.com](mailto:bozad@getxapi.com)

---

*GetXAPI is a Twitter / X data API service. Not affiliated with X Corp.*
