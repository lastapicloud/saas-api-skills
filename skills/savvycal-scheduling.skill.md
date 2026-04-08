---
name: savvycal-scheduling
description: Manage scheduling links and events via SavvyCal. Use when the user mentions
  savvycal, scheduling, calendar, event, booking, availability.
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
- get_by_id_events: Get event (GET /v1/events/{id})

## Fields

- `name`: string [REQUIRED for create]
- `duration`: integer [OPTIONAL]

## Example Request Bodies

**Create Link:**
```json
{"name": "30-Minute Meeting", "duration": 30}
```

**Update Link:**
```json
{"name": "45-Minute Consultation", "duration": 45}
```
