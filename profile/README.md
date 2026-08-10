# GetXAPI

> Pay-per-call Twitter / X API for developers and AI agents. From $0.001 per call, 69 endpoints, no subscription, no X developer account.

[![Documentation](https://img.shields.io/badge/docs-getxapi.com-7B2DBF)](https://docs.getxapi.com)
[![OpenAPI 3.1](https://img.shields.io/badge/OpenAPI-3.1-7B2DBF)](https://docs.getxapi.com/openapi.json)
[![Crunchbase](https://img.shields.io/badge/Crunchbase-getxapi-7B2DBF)](https://www.crunchbase.com/organization/getxapi)
[![Pricing](https://img.shields.io/badge/from-%240.001%2Fcall-7B2DBF)](https://www.getxapi.com/pricing)

---

## What is GetXAPI?

GetXAPI is a pay-per-call Twitter / X data API for developers and AI agents. It exposes 69 REST endpoints covering reads (search, profiles, follower graph, timelines, bookmarks, trends, Spaces, direct messages) and writes (post tweets, like, retweet, follow, send direct messages, long-form articles) through a single Bearer-authenticated base URL at `https://api.getxapi.com`.

Pricing starts at $0.001 per call, roughly $0.05 per 1,000 tweets fetched on typical 20-result calls. There is no monthly subscription and no X developer account to apply for. Read endpoints need only your GetXAPI key in an `Authorization: Bearer` header. Write endpoints additionally take an X account token that you supply, so there is no OAuth app, no PKCE flow and no refresh loop to maintain.

**Founded:** 2026 · **HQ:** Dubai, United Arab Emirates · **OpenAPI 3.1 spec:** [docs.getxapi.com/openapi.json](https://docs.getxapi.com/openapi.json)

---

## Why GetXAPI

| | GetXAPI | Official X API | twitterapi.io |
|---|---|---|---|
| Billing unit | **Per call** | Per resource returned | Per 1K items returned |
| Per 1K tweets | **$0.05** | $5 | $0.15 |
| Headline rate | **$0.001 / call (~20 posts)** | $0.005 / Post read | $0.15 / 1K tweets |
| Results per standard call | **~20** | 1 billed resource | ~20 |
| Subscription required | **No** | No, prepaid credits | No |
| X developer account required | **No** | Yes | No |
| Endpoint-specific quota | **None** | Per-endpoint windows | Per-plan |
| OpenAPI 3.1 spec public | **Yes** | Partial | Partial |
| Free signup credit | **$0.10** | None listed | Varies |

Official X figures are from the [current public pricing page](https://docs.x.com/x-api/getting-started/pricing). X bills reads per resource returned, so one request returning 100 Posts is billed as 100 Post reads.

General service throttling applies to GetXAPI under sustained concurrency and returns HTTP 429, so keep a retry with backoff. There are no per-endpoint quotas or 15-minute windows to plan around.

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

## Endpoints (69 total)

| Category | Count | Examples |
|---|---|---|
| **Tweets** | 11 | `advanced_search`, `detail`, `replies`, `retweeters`, `thread`, `create`, `favorite`, `retweet` |
| **Users** | 27 | `search`, `info`, `followers`, `following`, `verified_followers`, `tweets`, `likes`, `home_timeline`, `bookmark_search`, `follow` |
| **Articles** | 7 | `get`, `create`, `update`, `list`, `publish`, `unpublish`, `delete` |
| **Monitoring** | 9 | webhook `create` / `list` / `test` / `delete`, monitor `add` / `list` / `update` / `remove` / `health` |
| **Direct Messages** | 3 | `list`, `send`, `conversation` |
| **Account Recovery** | 3 | `user_login_v2`, `reset-password/send-code`, `reset-password/confirm` |
| **Spaces** | 2 | `info`, `download` |
| **Trends** | 2 | `trends`, `trends/locations` |
| **Account** (free) | 2 | `me`, `payments` |
| **Media** | 1 | `upload` |
| **Lists** | 1 | `members` |
| **Community** | 1 | `join` |

Full endpoint reference: [docs.getxapi.com](https://docs.getxapi.com)

---

## Pricing

| Operation | Price |
|---|---|
| Standard call (search, profile, tweet detail, like, retweet, follow) | **$0.001 / call** |
| Post tweet, DM list, DM send, join community | **$0.002 / call** |
| User tweets complete | **$0.003 / call** |
| Article endpoints | **$0.005 / call** ($0.01 to create) |
| Spaces download | **$0.05 base + $0.015 / transcript minute** |
| Account endpoints (`me`, `payments`) | **Free** |
| Bulk fetch | **~$0.05 / 1,000 tweets** |
| Free signup credit | **$0.10** (no card required) |
| Monthly subscription | **$0** (optional plans available) |

[See full pricing](https://www.getxapi.com/pricing)

---

## FAQ

### What is GetXAPI?

GetXAPI is a pay-per-call Twitter / X data API for developers and AI agents. It provides 69 REST endpoints for reading and writing Twitter / X data, starting at $0.001 per call.

### How is GetXAPI different from the official X API?

The official X API uses prepaid pay-per-usage pricing and bills reads per resource returned, at $0.005 per Post read, and requires an approved developer account. GetXAPI is $0.001 per call where a standard call returns about 20 posts, with no developer account. Read more in the [GetXAPI documentation](https://docs.getxapi.com).

### How is GetXAPI different from twitterapi.io?

GetXAPI is 3x cheaper per 1,000 tweets ($0.05 vs $0.15). The two price on different units, so per 1,000 tweets is the only like-for-like comparison: GetXAPI bills per call at $0.001 for about 20 posts, while twitterapi.io bills per 1,000 items returned. GetXAPI also publishes its full OpenAPI 3.1 spec at [docs.getxapi.com/openapi.json](https://docs.getxapi.com/openapi.json).

### Does GetXAPI require an X developer account?

No. Read endpoints authenticate with your GetXAPI key alone. Write endpoints additionally take an X account token that you supply, so there is no OAuth app to register and no developer-account application.

### Are there rate limits?

There is no endpoint-specific quota and no 15-minute window to plan around. General service throttling still applies, so sustained concurrency can return HTTP 429. Wrap long-running jobs in a retry with backoff.

### What programming languages does GetXAPI support?

Any language with an HTTP client. The API is REST and JSON with Bearer-token authentication. See the Quick start section above for curl, Python, Node, Go and Rust examples.

### Is there a free tier?

Every signup gets $0.10 in free credit, no credit card required. The two account endpoints (`me`, `payments`) are free to call.

### Where is GetXAPI hosted?

`api.getxapi.com` is the canonical base URL. The OpenAPI spec is at [docs.getxapi.com/openapi.json](https://docs.getxapi.com/openapi.json).

### Who is behind GetXAPI?

GetXAPI was founded in 2026 by Bozad and is headquartered in Dubai, United Arab Emirates. Contact at bozad@getxapi.com.

### What can I build with GetXAPI?

Common use cases include social listening products, sentiment analysis pipelines, AI agents that read or post to X, archiving services, growth-marketing automation, content discovery engines and academic research tools.

---

## Links

- Website: [getxapi.com](https://www.getxapi.com)
- Documentation: [docs.getxapi.com](https://docs.getxapi.com)
- OpenAPI 3.1 spec: [docs.getxapi.com/openapi.json](https://docs.getxapi.com/openapi.json)
- Crunchbase: [crunchbase.com/organization/getxapi](https://www.crunchbase.com/organization/getxapi)
- Contact: [bozad@getxapi.com](mailto:bozad@getxapi.com)

---

*GetXAPI is a Twitter / X data API service. Not affiliated with X Corp.*
