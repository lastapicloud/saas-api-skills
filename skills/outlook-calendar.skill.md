---
name: outlook-calendar
description: Manage calendar events via Outlook/Microsoft Graph. Use when the user
  mentions outlook, calendar, event, meeting, schedule, microsoft calendar.
version: 1.0.0
skill_type: external
base_url_env: OUTLOOK_CALENDAR_BASE_URL
auth_env_var: OUTLOOK_CALENDAR_ACCESS_TOKEN
auth_type: bearer
triggers:
  - outlook
  - calendar
  - event
  - meeting
  - schedule
  - microsoft calendar
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires OUTLOOK_CALENDAR_BASE_URL and OUTLOOK_CALENDAR_ACCESS_TOKEN
  environment variables.
---

# Outlook-Calendar

Manage calendar events via Outlook/Microsoft Graph. Use when the user mentions outlook, calendar, event, meeting, schedule, microsoft calendar.

## API Endpoints

- **GET** `/me/events` - List events
- **POST** `/me/events` - Create event
- **GET** `/me/events/{id}` - Get event
- **PATCH** `/me/events/{id}` - Update event
- **DELETE** `/me/events/{id}` - Delete event
- **GET** `/me/calendars` - List calendars
- **GET** `/me/calendarView` - Get calendar view
- **POST** `/me/findMeetingTimes` - Find meeting times

## Actions

- list: List events (GET /me/events)
- create: Create event (POST /me/events)
- get_by_id: Get event (GET /me/events/{id})
- update: Update event (PATCH /me/events/{id})
- delete: Delete event (DELETE /me/events/{id})
- list_calendars: List calendars (GET /me/calendars)
- list_calendarview: Get calendar view (GET /me/calendarView)
- create_findmeetingtimes: Find meeting times (POST /me/findMeetingTimes)

## Fields

- `subject`: string [REQUIRED for create]
- `start`: object [REQUIRED for create] (dateTime, timeZone)
- `end`: object [REQUIRED for create] (dateTime, timeZone)
- `attendees`: array [OPTIONAL]

## Example Request Bodies

**Create Event:**
```json
{"subject": "Team Standup", "start": {"dateTime": "2024-03-20T09:00:00", "timeZone": "America/New_York"}, "end": {"dateTime": "2024-03-20T09:30:00", "timeZone": "America/New_York"}, "attendees": [{"emailAddress": {"address": "colleague@example.com"}, "type": "required"}]}
```

**Find Meeting Times:**
```json
{"attendees": [{"emailAddress": {"address": "colleague@example.com"}}], "timeConstraint": {"timeslots": [{"start": {"dateTime": "2024-03-20T08:00:00", "timeZone": "UTC"}, "end": {"dateTime": "2024-03-20T18:00:00", "timeZone": "UTC"}}]}}
```
