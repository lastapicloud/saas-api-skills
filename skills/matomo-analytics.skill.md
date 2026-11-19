---
name: matomo-analytics
description: 'Track and analyze web traffic via Matomo. Use when the user mentions
  matomo, piwik, analytics, visitor, pageview, website analytics.

  '
version: 1.0.0
skill_type: external
base_url_env: MATOMO_BASE_URL
auth_env_var: MATOMO_API_TOKEN
auth_type: header
triggers:
  - matomo
  - piwik
  - analytics
  - visitor
  - pageview
  - website analytics
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires MATOMO_BASE_URL and MATOMO_API_TOKEN environment variables.
annotations:
  readOnlyHint: false
  destructiveHint: false
  idempotentHint: false
---

# Matomo-Analytics

Track and analyze web traffic via Matomo. Use when the user mentions matomo, piwik, analytics, visitor, pageview, website analytics.


## API Endpoints

- **GET** `/index.php?module=API&method=VisitsSummary.get` - Get visits summary
- **GET** `/index.php?module=API&method=Actions.getPageUrls` - Get page URLs
- **GET** `/index.php?module=API&method=Referrers.getWebsites` - Get referrers
- **GET** `/index.php?module=API&method=SitesManager.getAllSites` - List sites
- **GET** `/index.php?module=API&method=Live.getLastVisitsDetails` - Get live visits
- **POST** `/matomo.php` - Track pageview
- **GET** `/index.php?module=API&method=Goals.getGoals` - List goals

## Actions

- list: Get visits summary (GET /index.php?module=API&method=VisitsSummary.get)
- get_page_urls: Get page URLs (GET /index.php?module=API&method=Actions.getPageUrls)
- get_referrers: Get referrers (GET /index.php?module=API&method=Referrers.getWebsites)
- list_sites: List sites (GET /index.php?module=API&method=SitesManager.getAllSites)
- get_live_visits: Get live visits (GET /index.php?module=API&method=Live.getLastVisitsDetails)
- create: Track pageview (POST /matomo.php)
- list_goals: List goals (GET /index.php?module=API&method=Goals.getGoals)

## Fields

- `idSite`: integer [REQUIRED] — Idsite value
- `period`: string [REQUIRED] (day, week, month, year) — Period
- `date`: string [REQUIRED] — Date

## Example Request Bodies

**Track Pageview:**
```json
{"idsite": 1, "rec": 1, "url": "https://example.com/page", "action_name": "Homepage"}
```

**Query Report (via params):**
```json
{"idSite": 1, "period": "month", "date": "2024-01-01"}
```

## Response

**Index.Php?Module=Api&Method=Visitssummary.Get object:**
- `id`: string — Unique index.php?module=api&method=visitssummary.get identifier
- `name`: string — Index.Php?Module=Api&Method=Visitssummary.Get name or title
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
