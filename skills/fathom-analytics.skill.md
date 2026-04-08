---
name: fathom-analytics
description: Track website analytics via Fathom. Use when the user mentions fathom,
  analytics, pageview, visitor, website analytics.
version: 1.0.0
skill_type: external
base_url_env: FATHOM_BASE_URL
auth_env_var: FATHOM_API_KEY
auth_type: bearer
triggers:
  - fathom
  - analytics
  - pageview
  - visitor
  - website analytics
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires FATHOM_BASE_URL and FATHOM_API_KEY environment variables.
---

# Fathom-Analytics

Track website analytics via Fathom. Use when the user mentions fathom, analytics, pageview, visitor, website analytics.

## API Endpoints

- **GET** `/api/v1/sites` - List sites
- **POST** `/api/v1/sites` - Create site
- **GET** `/api/v1/sites/{site_id}` - Get site
- **DELETE** `/api/v1/sites/{site_id}` - Delete site
- **GET** `/api/v1/aggregations` - Get aggregated data
- **GET** `/api/v1/current_visitors` - Get current visitors
- **GET** `/api/v1/events` - List events
- **POST** `/api/v1/events` - Create event

## Actions

- list: List sites (GET /api/v1/sites)
- create: Create site (POST /api/v1/sites)
- get_by_id: Get site (GET /api/v1/sites/{site_id})
- delete: Delete site (DELETE /api/v1/sites/{site_id})
- list_aggregations: Get aggregated data (GET /api/v1/aggregations)
- list_current_visitors: Get current visitors (GET /api/v1/current_visitors)
- list_events: List events (GET /api/v1/events)
- create_events: Create event (POST /api/v1/events)

## Fields

- `name`: string [REQUIRED for create]
- `entity`: string [REQUIRED for aggregations] (pageview or event)
- `entity_id`: string [REQUIRED for aggregations]
- `date_from`: string [OPTIONAL]
- `date_to`: string [OPTIONAL]

## Example Request Bodies

**Create Site:**
```json
{"name": "My Website"}
```

**Create Event:**
```json
{"name": "Signup Button Click"}
