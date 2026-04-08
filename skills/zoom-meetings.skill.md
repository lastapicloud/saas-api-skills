---
name: zoom-meetings
description: Manage Zoom meetings, webinars, and users. Use when the user mentions
  zoom, meeting, webinar, video call, conference.
version: 1.0.0
skill_type: external
base_url_env: ZOOM_BASE_URL
auth_env_var: ZOOM_ACCESS_TOKEN
auth_type: bearer
triggers:
  - zoom
  - meeting
  - webinar
  - video call
  - conference
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires ZOOM_BASE_URL and ZOOM_ACCESS_TOKEN environment variables.
---

# Zoom-Meetings

Manage Zoom meetings, webinars, and users. Use when the user mentions zoom, meeting, webinar, video call, conference.

## API Endpoints

- **GET** `/v2/users` - List users
- **GET** `/v2/users/{userId}` - Get a user
- **GET** `/v2/users/{userId}/meetings` - List meetings
- **POST** `/v2/users/{userId}/meetings` - Create a meeting
- **GET** `/v2/meetings/{meetingId}` - Get a meeting
- **PATCH** `/v2/meetings/{meetingId}` - Update a meeting
- **DELETE** `/v2/meetings/{meetingId}` - Delete a meeting
- **GET** `/v2/users/{userId}/webinars` - List webinars
- **POST** `/v2/users/{userId}/webinars` - Create a webinar
- **GET** `/v2/past_meetings/{meetingId}/participants` - List participants
- **GET** `/app/api/rest/v1/account/balance` - balance
- **POST** `/app/api/rest/v1/account/transfer` - transfer
- **PUT** `/app/api/rest/v1/messages/{messageId}/markRead` - markRead
- **DELETE** `/app/api/rest/v1/contacts/{contactId}` - delete
- **GET** `/app/api/rest/v1/account/statistics` - statistics

## Actions

- list: List users (GET /v2/users)
- get_by_id: Get a user (GET /v2/users/{userId})
- list_meetings: List meetings (GET /v2/users/{userId}/meetings)
- create: Create a meeting (POST /v2/users/{userId}/meetings)
- get_by_id_meetings: Get a meeting (GET /v2/meetings/{meetingId})
- update: Update a meeting (PATCH /v2/meetings/{meetingId})
- delete: Delete a meeting (DELETE /v2/meetings/{meetingId})
- list_webinars: List webinars (GET /v2/users/{userId}/webinars)
- create_webinars: Create a webinar (POST /v2/users/{userId}/webinars)
- list_participants: List participants (GET /v2/past_meetings/{meetingId}/participants)
- list_balance: balance (GET /app/api/rest/v1/account/balance)
- create_transfer: transfer (POST /app/api/rest/v1/account/transfer)
- put_markread: markRead (PUT /app/api/rest/v1/messages/{messageId}/markRead)
- delete_contacts: delete (DELETE /app/api/rest/v1/contacts/{contactId})
- list_statistics: statistics (GET /app/api/rest/v1/account/statistics)

## Fields

- `topic`: string [REQUIRED for create]
- `type`: integer [REQUIRED] (1=instant, 2=scheduled, 3=recurring)
- `start_time`: string [REQUIRED for scheduled] (ISO datetime)
- `duration`: integer [OPTIONAL] (minutes)
- `timezone`: string [OPTIONAL]
- `agenda`: string [OPTIONAL]
- `password`: string [OPTIONAL]

## Example Request Bodies

**Create Meeting:**
```json
{"topic": "Sprint Planning", "type": 2, "start_time": "2026-03-25T10:00:00Z", "duration": 60, "timezone": "America/New_York", "agenda": "Review backlog and assign tasks"}
```

**Create Webinar:**
```json
{"topic": "Product Launch Webinar", "type": 5, "start_time": "2026-04-01T14:00:00Z", "duration": 90}
```
