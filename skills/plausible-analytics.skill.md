---
name: plausible-analytics
description: 'Query Plausible Analytics stats and manage sites. Use when the user
  mentions plausible, analytics, stats, visitors, pageview.

  '
version: 1.0.0
skill_type: external
base_url_env: PLAUSIBLE_BASE_URL
auth_env_var: PLAUSIBLE_API_KEY
auth_type: bearer
triggers:
  - plausible
  - analytics
  - stats
  - visitors
  - pageview
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires PLAUSIBLE_BASE_URL and PLAUSIBLE_API_KEY environment variables.
annotations:
  readOnlyHint: false
  destructiveHint: true
  idempotentHint: false
---

# Plausible-Analytics

Query Plausible Analytics stats and manage sites. Use when the user mentions plausible, analytics, stats, visitors, pageview.


## API Endpoints

- **GET** `/api/v1/stats/realtime/visitors` - Get real-time visitors
- **GET** `/api/v1/stats/aggregate` - Get aggregate stats
- **GET** `/api/v1/stats/timeseries` - Get timeseries data
- **GET** `/api/v1/stats/breakdown` - Get breakdown by property
- **GET** `/api/v2/query` - Run a query (v2)
- **GET** `/api/v1/sites` - List sites
- **POST** `/api/v1/sites` - Create a site
- **DELETE** `/api/v1/sites/{siteId}` - Delete a site
- **PUT** `/api/v1/sites/shared-links` - Create a shared link
- **PUT** `/api/v1/sites/goals` - Create a goal

## Actions

- list: Get real-time visitors (GET /api/v1/stats/realtime/visitors)
- get_aggregate_stats: Get aggregate stats (GET /api/v1/stats/aggregate)
- get_timeseries_data: Get timeseries data (GET /api/v1/stats/timeseries)
- get_breakdown_property: Get breakdown by property (GET /api/v1/stats/breakdown)
- query: Run a query (v2) (GET /api/v2/query)
- list_sites: List sites (GET /api/v1/sites)
- create: Create a site (POST /api/v1/sites)
- delete: Delete a site (DELETE /api/v1/sites/{siteId})
- put_shared_links: Create a shared link (PUT /api/v1/sites/shared-links)
- put_goals: Create a goal (PUT /api/v1/sites/goals)

## Fields

- `site_id`: string [REQUIRED for stats queries] — Site unique identifier
- `period`: string [OPTIONAL] ("day", "7d", "30d", "month", "6mo", "12mo", "custom") — Period
- `metrics`: string [OPTIONAL] ("visitors,pageviews,bounce_rate,visit_duration") — Metrics
- `property`: string [REQUIRED for breakdown] (e.g., "visit:source", "visit:country") — Property
- `domain`: string [REQUIRED for create site] — Domain

## Example Request Bodies

**Create Site:**
```json
{"domain": "mywebsite.com"}
```

**Get Aggregate Stats (query params):**
```json
{"site_id": "mywebsite.com", "period": "30d", "metrics": "visitors,pageviews,bounce_rate"}
```

## Response

**Site object:**
- `id`: string — Unique site identifier
- `name`: string — Site name or title
- `status`: string — Current status
- `created_at`: string — Creation timestamp (ISO 8601)
- `updated_at`: string — Last update timestamp (ISO 8601)

## Error Responses

| Status | Meaning |
|--------|---------|
| 400 | Invalid request body — check required fields and types |
| 401 | Authentication failed — verify API key or token is valid and not expired |
| 403 | Forbidden — insufficient permissions or scope for this action |
| 404 | Resource not found — check the ID or identifier |
| 409 | Conflict — resource already exists or concurrent modification |
| 429 | Rate limited — too many requests, retry after delay |
| 500 | Server error — retry or check service status page |
