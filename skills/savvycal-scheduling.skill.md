---
name: savvycal-scheduling
description: 'Manage scheduling links and events via SavvyCal. Use when the user mentions
  savvycal, scheduling, calendar, event, booking, availability.

  '
version: 1.0.0
skill_type: external
base_url_env: SAVVYCAL_BASE_URL
auth_env_var: SAVVYCAL_API_TOKEN
auth_type: bearer
triggers:
  - savvycal
  - scheduling
  - calendar
  - event
  - booking
  - availability
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires SAVVYCAL_BASE_URL and SAVVYCAL_API_TOKEN environment variables.
annotations:
  readOnlyHint: false
  destructiveHint: true
  idempotentHint: false
---

# Savvycal-Scheduling

Manage scheduling links and events via SavvyCal. Use when the user mentions savvycal, scheduling, calendar, event, booking, availability.


## API Endpoints

- **GET** `/v1/links` - List links
- **POST** `/v1/links` - Create link
- **GET** `/v1/links/{id}` - Get link
- **PATCH** `/v1/links/{id}` - Update link
- **DELETE** `/v1/links/{id}` - Delete link
- **GET** `/v1/events` - List events
- **GET** `/v1/events/{id}` - Get event

## Actions

- list: List links (GET /v1/links)
- create: Create link (POST /v1/links)
- get_by_id: Get link (GET /v1/links/{id})
- update: Update link (PATCH /v1/links/{id})
- delete: Delete link (DELETE /v1/links/{id})
- list_events: List events (GET /v1/events)
- get_event: Get event (GET /v1/events/{id})

## Fields

- `name`: string [REQUIRED for create] — Display name
- `duration`: integer [OPTIONAL] — Duration value

## Example Request Bodies

**Create Link:**
```json
{"name": "30-Minute Meeting", "duration": 30}
```

**Update Link:**
```json
{"name": "45-Minute Consultation", "duration": 45}
```

## Response

**Link object:**
- `id`: string — Unique link identifier
- `name`: string — Link name or title
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
