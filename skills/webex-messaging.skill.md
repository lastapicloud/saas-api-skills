---
name: webex-messaging
description: Send messages and manage Webex rooms and meetings. Use when the user
  mentions webex, cisco, message, room, meeting, space.
version: 1.0.0
skill_type: external
base_url_env: WEBEX_BASE_URL
auth_env_var: WEBEX_ACCESS_TOKEN
auth_type: bearer
triggers:
  - webex
  - cisco
  - message
  - room
  - meeting
  - space
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires WEBEX_BASE_URL and WEBEX_ACCESS_TOKEN environment variables.
---

# Webex-Messaging

Send messages and manage Webex rooms and meetings. Use when the user mentions webex, cisco, message, room, meeting, space.

## API Endpoints

- **POST** `/v1/messages` - Send a message
- **GET** `/v1/messages` - List messages
- **GET** `/v1/messages/{messageId}` - Get a message
- **DELETE** `/v1/messages/{messageId}` - Delete a message
- **GET** `/v1/rooms` - List rooms
- **POST** `/v1/rooms` - Create a room
- **GET** `/v1/people` - List people
- **GET** `/v1/people/me` - Get current user
- **POST** `/v1/meetings` - Create a meeting
- **GET** `/v1/meetings` - List meetings
- **PUT** `/v1/rooms/{roomId}` - Update a room

## Actions

- create: Send a message (POST /v1/messages)
- list: List messages (GET /v1/messages)
- get_by_id: Get a message (GET /v1/messages/{messageId})
- delete: Delete a message (DELETE /v1/messages/{messageId})
- list_rooms: List rooms (GET /v1/rooms)
- create_rooms: Create a room (POST /v1/rooms)
- list_people: List people (GET /v1/people)
- list_me: Get current user (GET /v1/people/me)
- create_meetings: Create a meeting (POST /v1/meetings)
- list_meetings: List meetings (GET /v1/meetings)
- update: Update a room (PUT /v1/rooms/{roomId})

## Fields

- `roomId`: string [REQUIRED for send message]
- `text`: string [REQUIRED for send message]
- `markdown`: string [OPTIONAL]
- `title`: string [REQUIRED for create room/meeting]
- `start`: string (datetime) [REQUIRED for create meeting]
- `end`: string (datetime) [REQUIRED for create meeting]

## Example Request Bodies

**Send Message:**
```json
{"roomId": "Y2lzY29zcGFyazov...", "text": "Hello team!", "markdown": "**Hello** team!"}
```

**Create Meeting:**
```json
{"title": "Sprint Planning", "start": "2026-03-25T10:00:00Z", "end": "2026-03-25T11:00:00Z"}
```
