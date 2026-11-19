---
name: outlookcalendar-scheduling
description: 'Manage Outlook Calendar events and calendars. Use when the user mentions
  outlook, outlook calendar, event, meeting, calendar, schedule.

  '
version: 1.0.0
skill_type: external
base_url_env: OUTLOOK_CALENDAR_BASE_URL
auth_env_var: MICROSOFT_GRAPH_TOKEN
auth_type: bearer
triggers:
  - outlook
  - outlook calendar
  - event
  - meeting
  - calendar
  - schedule
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: 'Requires OUTLOOK_CALENDAR_BASE_URL and MICROSOFT_GRAPH_TOKEN environment
  variables.

  '
annotations:
  readOnlyHint: false
  destructiveHint: true
  idempotentHint: false
---

# Outlookcalendar-Scheduling

Manage Outlook Calendar events and calendars. Use when the user mentions outlook, outlook calendar, event, meeting, calendar, schedule.


## API Endpoints

- **GET** `/v1.0/me/events` - List events
- **GET** `/v1.0/me/events/{eventId}` - Get an event
- **POST** `/v1.0/me/events` - Create an event
- **PATCH** `/v1.0/me/events/{eventId}` - Update an event
- **DELETE** `/v1.0/me/events/{eventId}` - Delete an event
- **GET** `/v1.0/me/calendars` - List calendars
- **POST** `/v1.0/me/calendars` - Create a calendar
- **GET** `/v1.0/me/calendarView` - Get calendar view
- **POST** `/v1.0/me/findMeetingTimes` - Find meeting times

## Actions

- list: List events (GET /v1.0/me/events)
- get_by_id: Get an event (GET /v1.0/me/events/{eventId})
- create: Create an event (POST /v1.0/me/events)
- update: Update an event (PATCH /v1.0/me/events/{eventId})
- delete: Delete an event (DELETE /v1.0/me/events/{eventId})
- list_calendars: List calendars (GET /v1.0/me/calendars)
- create_calendar: Create a calendar (POST /v1.0/me/calendars)
- get_calendar_view: Get calendar view (GET /v1.0/me/calendarView)
- create_find_meeting_times: Find meeting times (POST /v1.0/me/findMeetingTimes)

## Fields

- `subject`: string [REQUIRED for create] — Subject
- `start`: object [REQUIRED] with `dateTime`, `timeZone` — Start configuration
- `end`: object [REQUIRED] with `dateTime`, `timeZone` — End configuration
- `body`: object [OPTIONAL] with `contentType`, `content` — Request body content
- `attendees`: array [OPTIONAL] with `emailAddress`, `type` — List of attendees
- `location`: object [OPTIONAL] with `displayName` — Location configuration

## Example Request Bodies

**Create Event:**
```json
{"subject": "Project Review", "start": {"dateTime": "2024-03-25T14:00:00", "timeZone": "America/Chicago"}, "end": {"dateTime": "2024-03-25T15:00:00", "timeZone": "America/Chicago"}, "body": {"contentType": "HTML", "content": "Quarterly project review meeting"}, "location": {"displayName": "Conference Room A"}}
```

**Create Calendar:**
```json
{"name": "Team Events"}
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
