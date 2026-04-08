---
name: google-calendar
description: Manage events and calendars in Google Calendar. Use when the user mentions
  calendar, google calendar, event, meeting, schedule, appointment.
version: 1.0.0
skill_type: external
base_url_env: GOOGLE_CALENDAR_BASE_URL
auth_env_var: GOOGLE_API_TOKEN
auth_type: bearer
triggers:
  - calendar
  - google calendar
  - event
  - meeting
  - schedule
  - appointment
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires GOOGLE_CALENDAR_BASE_URL and GOOGLE_API_TOKEN environment
  variables.
---

# Google-Calendar

Manage events and calendars in Google Calendar. Use when the user mentions calendar, google calendar, event, meeting, schedule, appointment.

## API Endpoints

- **GET** `/calendars/{calendarId}/events` - List events
- **POST** `/calendars/{calendarId}/events` - Create an event
- **PATCH** `/calendars/{calendarId}/events/{eventId}` - Update an event
- **DELETE** `/calendars/{calendarId}/events/{eventId}` - Delete an event
- **GET** `/users/me/calendarList` - List calendars
- **POST** `/freeBusy` - Get free/busy information
- **DELETE** `/calendars/calendarId/acl/ruleId`
- **GET** `/calendars/calendarId/acl/ruleId`
- **POST** `/calendars/calendarId/acl`
- **GET** `/calendars/calendarId/acl`
- **PATCH** `/calendars/calendarId/acl/ruleId`
- **PUT** `/calendars/calendarId/acl/ruleId`
- **POST** `/calendars/calendarId/acl/watch`
- **DELETE** `/users/me/calendarList/calendarId`
- **GET** `/users/me/calendarList/calendarId`

## Actions

- list: List events (GET /calendars/{calendarId}/events)
- create: Create an event (POST /calendars/{calendarId}/events)
- update: Update an event (PATCH /calendars/{calendarId}/events/{eventId})
- delete: Delete an event (DELETE /calendars/{calendarId}/events/{eventId})
- list_calendarlist: List calendars (GET /users/me/calendarList)
- create_freebusy: Get free/busy information (POST /freeBusy)
- delete_ruleid: DELETE /calendars/calendarId/acl/ruleId (DELETE /calendars/calendarId/acl/ruleId)
- list_ruleid: GET /calendars/calendarId/acl/ruleId (GET /calendars/calendarId/acl/ruleId)
- create_acl: POST /calendars/calendarId/acl (POST /calendars/calendarId/acl)
- list_acl: GET /calendars/calendarId/acl (GET /calendars/calendarId/acl)
- patch_ruleid: PATCH /calendars/calendarId/acl/ruleId (PATCH /calendars/calendarId/acl/ruleId)
- put_ruleid: PUT /calendars/calendarId/acl/ruleId (PUT /calendars/calendarId/acl/ruleId)
- create_watch: POST /calendars/calendarId/acl/watch (POST /calendars/calendarId/acl/watch)
- delete_calendarid: DELETE /users/me/calendarList/calendarId (DELETE /users/me/calendarList/calendarId)
- list_calendarid: GET /users/me/calendarList/calendarId (GET /users/me/calendarList/calendarId)

## Fields

- `calendarId`: string [REQUIRED for event actions] (calendar ID, use "primary" for the default calendar)
- `eventId`: string [REQUIRED for update_event, delete_event] (event ID)
- `summary`: string [REQUIRED for create_event] (event title)
- `start`: object [REQUIRED for create_event] (start time, e.g. {"dateTime": "...", "timeZone": "..."})
- `end`: object [REQUIRED for create_event] (end time, e.g. {"dateTime": "...", "timeZone": "..."})
- `description`: string [OPTIONAL] (event description)
- `location`: string [OPTIONAL] (event location)
- `attendees`: array of objects [OPTIONAL] (e.g. [{"email": "user@example.com"}])
- `timeMin`: string [OPTIONAL for list_events] (lower bound for event start time, RFC3339)
- `timeMax`: string [OPTIONAL for list_events] (upper bound for event start time, RFC3339)

## Example Request Bodies

**Create Event:**
```json
{"summary": "Team Standup", "start": {"dateTime": "2026-03-24T09:00:00", "timeZone": "America/New_York"}, "end": {"dateTime": "2026-03-24T09:30:00", "timeZone": "America/New_York"}, "attendees": [{"email": "user@example.com"}]}
```

**Get Free/Busy:**
```json
{"timeMin": "2026-03-24T00:00:00Z", "timeMax": "2026-03-25T00:00:00Z", "items": [{"id": "primary"}]}
```
