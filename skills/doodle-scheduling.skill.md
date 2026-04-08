---
name: doodle-scheduling
description: Create and manage polls and scheduling via Doodle. Use when the user
  mentions doodle, poll, scheduling, meeting, availability.
version: 1.0.0
skill_type: external
base_url_env: DOODLE_BASE_URL
auth_env_var: DOODLE_API_KEY
auth_type: bearer
triggers:
  - doodle
  - poll
  - scheduling
  - meeting
  - availability
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires DOODLE_BASE_URL and DOODLE_API_KEY environment variables.
---

# Doodle-Scheduling

Create and manage polls and scheduling via Doodle. Use when the user mentions doodle, poll, scheduling, meeting, availability.

## API Endpoints

- **GET** `/api/v2.1/polls` - List polls
- **POST** `/api/v2.1/polls` - Create a poll
- **GET** `/api/v2.1/polls/{pollId}` - Get poll by ID
- **PUT** `/api/v2.1/polls/{pollId}` - Update a poll
- **DELETE** `/api/v2.1/polls/{pollId}` - Delete a poll
- **GET** `/api/v2.1/polls/{pollId}/participants` - List participants
- **POST** `/api/v2.1/polls/{pollId}/participants` - Add a participant

## Actions

- list: List polls (GET /api/v2.1/polls)
- create: Create a poll (POST /api/v2.1/polls)
- get_by_id: Get poll by ID (GET /api/v2.1/polls/{pollId})
- update: Update a poll (PUT /api/v2.1/polls/{pollId})
- delete: Delete a poll (DELETE /api/v2.1/polls/{pollId})
- list_participants: List participants (GET /api/v2.1/polls/{pollId}/participants)
- create_participants: Add a participant (POST /api/v2.1/polls/{pollId}/participants)

## Fields

- `title`: string [REQUIRED for create]
- `options`: array [REQUIRED for create] (date/time options)
- `type`: string [OPTIONAL]

## Example Request Bodies

**Create Poll:**
```json
{"title": "Team Standup Time", "options": [{"date": "2025-07-01T09:00:00Z"}, {"date": "2025-07-01T10:00:00Z"}]}
```

**Add Participant:**
```json
{"name": "Jane Doe", "preferences": [{"optionId": "opt_1", "preference": 1}]}
