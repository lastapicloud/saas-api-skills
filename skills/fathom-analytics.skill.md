---
name: fathom-analytics
description: 'Track website analytics via Fathom. Use when the user mentions fathom,
  analytics, pageview, visitor, website analytics.

  '
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
annotations:
  readOnlyHint: false
  destructiveHint: true
  idempotentHint: false
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
- get_aggregated_data: Get aggregated data (GET /api/v1/aggregations)
- get_current_visitors: Get current visitors (GET /api/v1/current_visitors)
- list_events: List events (GET /api/v1/events)
- create_event: Create event (POST /api/v1/events)

## Fields

- `name`: string [REQUIRED for create] — Display name
- `entity`: string [REQUIRED for aggregations] (pageview or event) — Entity
- `entity_id`: string [REQUIRED for aggregations] — Entity unique identifier
- `date_from`: string [OPTIONAL] — Date From
- `date_to`: string [OPTIONAL] — Date To

## Example Request Bodies

**Create Site:**
```json
{"name": "My Website"}
```

**Create Event:**
```json
{"name": "Signup Button Click"}

## Response

**Site object:**
- `id`: string — Unique site identifier
- `name`: string — Site name or title
- `status`: string — Current status
- `created_at`: string — Creation timestamp (ISO 8601)
- `updated_at`: string — Last update timestamp (ISO 8601)


**Required fields reference:**
```json
{
  "entity": "example_entity",
  "entity_id": "example_entity_id"
}
```


**Required fields reference:**
```json
{
  "entity": "example_entity",
  "entity_id": "example_entity_id"
}
```

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
