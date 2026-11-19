---
name: cronofy-scheduling
description: 'Manage Cronofy calendars, events, and availability. Use when the user
  mentions cronofy, calendar, event, availability, scheduling.

  '
version: 1.0.0
skill_type: external
base_url_env: CRONOFY_BASE_URL
auth_env_var: CRONOFY_ACCESS_TOKEN
auth_type: bearer
triggers:
  - cronofy
  - calendar
  - event
  - availability
  - scheduling
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires CRONOFY_BASE_URL and CRONOFY_ACCESS_TOKEN environment variables.
annotations:
  readOnlyHint: false
  destructiveHint: true
  idempotentHint: false
---

# Cronofy-Scheduling

Manage Cronofy calendars, events, and availability. Use when the user mentions cronofy, calendar, event, availability, scheduling.


## API Endpoints

- **GET** `/v1/calendars` - List calendars
- **GET** `/v1/events` - Read events
- **POST** `/v1/calendars/{calendarId}/events` - Create/update an event
- **DELETE** `/v1/calendars/{calendarId}/events` - Delete an event
- **POST** `/v1/availability` - Query availability
- **GET** `/v1/free_busy` - Get free/busy info
- **POST** `/v1/real_time_scheduling` - Create real-time scheduling link
- **GET** `/v1/userinfo` - Get user info
- **GET** `/v1/profiles` - List calendar profiles

## Actions

- list: List calendars (GET /v1/calendars)
- get_read_events: Read events (GET /v1/events)
- create: Create/update an event (POST /v1/calendars/{calendarId}/events)
- delete_events: Delete an event (DELETE /v1/calendars/{calendarId}/events)
- create_query_availability: Query availability (POST /v1/availability)
- get_freebusy_info: Get free/busy info (GET /v1/free_busy)
- create_realtime_scheduling_link: Create real-time scheduling link (POST /v1/real_time_scheduling)
- get_user_info: Get user info (GET /v1/userinfo)
- list_calendar_profiles: List calendar profiles (GET /v1/profiles)

## Fields

- `event_id`: string [REQUIRED for create/delete event] — Event unique identifier
- `summary`: string [REQUIRED for create event] — Summary
- `start`: string [REQUIRED] (ISO datetime) — Start
- `end`: string [REQUIRED] (ISO datetime) — End
- `participants`: array [REQUIRED for availability] with `required` sub-arrays of `sub` IDs — List of participants

## Example Request Bodies

**Create Event:**
```json
{"event_id": "evt-meeting-001", "summary": "Product roadmap review", "start": "2026-04-15T14:00:00Z", "end": "2026-04-15T15:00:00Z"}
```

**Query Availability:**
```json
{"participants": [{"members": [{"sub": "acc_001"}], "required": "all"}], "required_duration": {"minutes": 30}, "available_periods": [{"start": "2026-04-15T09:00:00Z", "end": "2026-04-15T17:00:00Z"}]}
```

## Response

**Event object:**
- `id`: string — Unique event identifier
- `name`: string — Event name or title
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
