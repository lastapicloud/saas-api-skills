---
name: slite-wiki
description: Manage Slite notes, channels, and collections. Use when the user mentions
  slite, note, wiki, documentation, channel.
version: 1.0.0
skill_type: external
base_url_env: SLITE_BASE_URL
auth_env_var: SLITE_API_TOKEN
auth_type: bearer
triggers:
  - slite
  - note
  - wiki
  - documentation
  - channel
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires SLITE_BASE_URL and SLITE_API_TOKEN environment variables.
---

# Slite-Wiki

Manage Slite notes, channels, and collections. Use when the user mentions slite, note, wiki, documentation, channel.

## API Endpoints

- **GET** `/v1/notes` - List notes
- **GET** `/v1/notes/{noteId}` - Get a note
- **POST** `/v1/notes` - Create a note
- **PUT** `/v1/notes/{noteId}` - Update a note
- **DELETE** `/v1/notes/{noteId}` - Delete a note
- **POST** `/v1/ask` - Ask a question (AI-powered)
- **GET** `/v1/channels` - List channels
- **GET** `/v1/users` - List users

## Actions

- list: List notes (GET /v1/notes)
- get_by_id: Get a note (GET /v1/notes/{noteId})
- create: Create a note (POST /v1/notes)
- update: Update a note (PUT /v1/notes/{noteId})
- delete: Delete a note (DELETE /v1/notes/{noteId})
- create_ask: Ask a question (AI-powered) (POST /v1/ask)
- list_channels: List channels (GET /v1/channels)
- list_users: List users (GET /v1/users)

## Fields

- `title`: string [REQUIRED for create]
- `markdown`: string [OPTIONAL]
- `parentNoteId`: string [OPTIONAL]
- `question`: string [REQUIRED for ask]

## Example Request Bodies

**Create Note:**
```json
{"title": "Onboarding Guide", "markdown": "# Welcome\nFollow these steps to get started."}
```

**Ask Question:**
```json
{"question": "What is our deployment process?"}
```
