---
name: outlookcalendar-scheduling
description: Manage Outlook Calendar events and calendars. Use when the user mentions
  outlook, outlook calendar, event, meeting, calendar, schedule.
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
compatibility: Requires OUTLOOK_CALENDAR_BASE_URL and MICROSOFT_GRAPH_TOKEN environment
  variables.
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
- create_calendars: Create a calendar (POST /v1.0/me/calendars)
- list_calendarview: Get calendar view (GET /v1.0/me/calendarView)
- create_findmeetingtimes: Find meeting times (POST /v1.0/me/findMeetingTimes)

## Fields

- `subject`: string [REQUIRED for create]
- `start`: object [REQUIRED] with `dateTime`, `timeZone`
- `end`: object [REQUIRED] with `dateTime`, `timeZone`
- `body`: object [OPTIONAL] with `contentType`, `content`
- `attendees`: array [OPTIONAL] with `emailAddress`, `type`
- `location`: object [OPTIONAL] with `displayName`

## Example Request Bodies

**Create Event:**
```json
{"subject": "Project Review", "start": {"dateTime": "2024-03-25T14:00:00", "timeZone": "America/Chicago"}, "end": {"dateTime": "2024-03-25T15:00:00", "timeZone": "America/Chicago"}, "body": {"contentType": "HTML", "content": "<p>Quarterly project review meeting</p>"}, "location": {"displayName": "Conference Room A"}}
```

**Create Calendar:**
```json
{"name": "Team Events"}
```
