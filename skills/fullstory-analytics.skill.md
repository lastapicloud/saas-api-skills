---
name: fullstory-analytics
description: 'Track user sessions and events via FullStory. Use when the user mentions
  fullstory, session, replay, analytics, user experience, heatmap.

  '
version: 1.0.0
skill_type: external
base_url_env: FULLSTORY_BASE_URL
auth_env_var: FULLSTORY_API_KEY
auth_type: header
triggers:
  - fullstory
  - session
  - replay
  - analytics
  - user experience
  - heatmap
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires FULLSTORY_BASE_URL and FULLSTORY_API_KEY environment variables.
annotations:
  readOnlyHint: false
  destructiveHint: false
  idempotentHint: false
---

# Fullstory-Analytics

Track user sessions and events via FullStory. Use when the user mentions fullstory, session, replay, analytics, user experience, heatmap.


## API Endpoints

- **POST** `/v2/segments` - Create segment
- **GET** `/v2/segments` - List segments
- **POST** `/v2/events` - Create custom event
- **GET** `/v2/sessions` - Search sessions
- **POST** `/v2/users` - Create or update user
- **GET** `/v2/users/{uid}` - Get user
- **POST** `/v2/search/events` - Search events
- **GET** `/v2/data-export/list` - List data exports

## Actions

- create: Create segment (POST /v2/segments)
- list: List segments (GET /v2/segments)
- create_custom_event: Create custom event (POST /v2/events)
- search_sessions: Search sessions (GET /v2/sessions)
- create_update_user: Create or update user (POST /v2/users)
- get_by_id: Get user (GET /v2/users/{uid})
- search_events: Search events (POST /v2/search/events)
- list_data_exports: List data exports (GET /v2/data-export/list)

## Fields

- `uid`: string [REQUIRED for create_user] — U unique identifier
- `display_name`: string [OPTIONAL] — Display display name
- `email`: string [OPTIONAL] — Email address

## Example Request Bodies

**Create/Update User:**
```json
{"uid": "user_abc123", "display_name": "Jane Smith", "email": "jane@example.com"}
```

**Search Events:**
```json
{"filter": {"type": "event", "event_name": "purchase"}, "start": "2025-01-01", "end": "2025-06-30"}

## Response

**Segment object:**
- `id`: string — Unique segment identifier
- `name`: string — Segment name or title
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
