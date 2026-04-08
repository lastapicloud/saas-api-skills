---
name: nylas-email
description: Manage emails, calendars, and contacts via Nylas. Use when the user mentions
  nylas, email, calendar, contact, inbox, scheduling.
version: 1.0.0
skill_type: external
base_url_env: NYLAS_BASE_URL
auth_env_var: NYLAS_API_KEY
auth_type: bearer
triggers:
  - nylas
  - email
  - calendar
  - contact
  - inbox
  - scheduling
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires NYLAS_BASE_URL and NYLAS_API_KEY environment variables.
---

# Nylas-Email

Manage emails, calendars, and contacts via Nylas. Use when the user mentions nylas, email, calendar, contact, inbox, scheduling.

## API Endpoints

- **GET** `/v3/grants/{grantId}/messages` - List messages
- **GET** `/v3/grants/{grantId}/messages/{messageId}` - Get message
- **POST** `/v3/grants/{grantId}/messages/send` - Send message
- **GET** `/v3/grants/{grantId}/events` - List events
- **POST** `/v3/grants/{grantId}/events` - Create event
- **GET** `/v3/grants/{grantId}/contacts` - List contacts
- **POST** `/v3/grants/{grantId}/contacts` - Create contact
- **GET** `/v3/grants/{grantId}/calendars` - List calendars

## Actions

- list: List messages (GET /v3/grants/{grantId}/messages)
- get_by_id: Get message (GET /v3/grants/{grantId}/messages/{messageId})
- create: Send message (POST /v3/grants/{grantId}/messages/send)
- list_events: List events (GET /v3/grants/{grantId}/events)
- create_events: Create event (POST /v3/grants/{grantId}/events)
- list_contacts: List contacts (GET /v3/grants/{grantId}/contacts)
- create_contacts: Create contact (POST /v3/grants/{grantId}/contacts)
- list_calendars: List calendars (GET /v3/grants/{grantId}/calendars)

## Fields

- `to`: array [REQUIRED for send]
- `subject`: string [REQUIRED for send]
- `body`: string [REQUIRED for send]
- `grantId`: string [REQUIRED]

## Example Request Bodies

**Send Message:**
```json
{"to": [{"email": "recipient@example.com", "name": "Jane Smith"}], "subject": "Project Update", "body": "Hi Jane, here is the latest update on the project."}
```

**Create Event:**
```json
{"title": "Team Standup", "when": {"start_time": 1700000000, "end_time": 1700003600}, "participants": [{"email": "team@example.com"}]}
```
