---
name: cronofy-scheduling
description: Manage Cronofy calendars, events, and availability. Use when the user
  mentions cronofy, calendar, event, availability, scheduling.
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
- list_events: Read events (GET /v1/events)
- create: Create/update an event (POST /v1/calendars/{calendarId}/events)
- delete_events: Delete an event (DELETE /v1/calendars/{calendarId}/events)
- create_availability: Query availability (POST /v1/availability)
- list_free_busy: Get free/busy info (GET /v1/free_busy)
- create_real_time_scheduling: Create real-time scheduling link (POST /v1/real_time_scheduling)
- list_userinfo: Get user info (GET /v1/userinfo)
- list_profiles: List calendar profiles (GET /v1/profiles)

## Fields

- `event_id`: string [REQUIRED for create/delete event]
- `summary`: string [REQUIRED for create event]
- `start`: string [REQUIRED] (ISO datetime)
- `end`: string [REQUIRED] (ISO datetime)
- `participants`: array [REQUIRED for availability] with `required` sub-arrays of `sub` IDs

## Example Request Bodies

**Create Event:**
```json
{"event_id": "evt-meeting-001", "summary": "Product roadmap review", "start": "2026-04-15T14:00:00Z", "end": "2026-04-15T15:00:00Z"}
```

**Query Availability:**
```json
{"participants": [{"members": [{"sub": "acc_001"}], "required": "all"}], "required_duration": {"minutes": 30}, "available_periods": [{"start": "2026-04-15T09:00:00Z", "end": "2026-04-15T17:00:00Z"}]}
```
