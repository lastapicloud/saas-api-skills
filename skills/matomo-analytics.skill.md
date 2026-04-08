---
name: matomo-analytics
description: Track and analyze web traffic via Matomo. Use when the user mentions
  matomo, piwik, analytics, visitor, pageview, website analytics.
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
- list_index_phpmoduleapimethodactions_getpageurls: Get page URLs (GET /index.php?module=API&method=Actions.getPageUrls)
- list_index_phpmoduleapimethodreferrers_getwebsites: Get referrers (GET /index.php?module=API&method=Referrers.getWebsites)
- list_index_phpmoduleapimethodsitesmanager_getallsites: List sites (GET /index.php?module=API&method=SitesManager.getAllSites)
- list_index_phpmoduleapimethodlive_getlastvisitsdetails: Get live visits (GET /index.php?module=API&method=Live.getLastVisitsDetails)
- create: Track pageview (POST /matomo.php)
- list_index_phpmoduleapimethodgoals_getgoals: List goals (GET /index.php?module=API&method=Goals.getGoals)

## Fields

- `idSite`: integer [REQUIRED]
- `period`: string [REQUIRED] (day, week, month, year)
- `date`: string [REQUIRED]

## Example Request Bodies

**Track Pageview:**
```json
{"idsite": 1, "rec": 1, "url": "https://example.com/page", "action_name": "Homepage"}
```

**Query Report (via params):**
```json
{"idSite": 1, "period": "month", "date": "2024-01-01"}
```
