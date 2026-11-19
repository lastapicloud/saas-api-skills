---
name: mattermost-messaging
description: 'Manage channels and messages via Mattermost. Use when the user mentions
  mattermost, channel, message, team, chat.

  '
version: 1.0.0
skill_type: external
base_url_env: MATTERMOST_BASE_URL
auth_env_var: MATTERMOST_ACCESS_TOKEN
auth_type: bearer
triggers:
  - mattermost
  - channel
  - message
  - team
  - chat
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires MATTERMOST_BASE_URL and MATTERMOST_ACCESS_TOKEN environment
  variables.
annotations:
  readOnlyHint: false
  destructiveHint: true
  idempotentHint: false
---

# Mattermost-Messaging

Manage channels and messages via Mattermost. Use when the user mentions mattermost, channel, message, team, chat.


## API Endpoints

- **GET** `/api/v4/channels` - List channels
- **POST** `/api/v4/channels` - Create channel
- **GET** `/api/v4/channels/{channel_id}` - Get channel
- **DELETE** `/api/v4/channels/{channel_id}` - Delete channel
- **POST** `/api/v4/posts` - Create post
- **GET** `/api/v4/channels/{channel_id}/posts` - List posts
- **GET** `/api/v4/teams` - List teams
- **GET** `/api/v4/users` - List users
- **PUT** `/api/v4/channels/{channel_id}` - Update channel
- **PATCH** `/api/v4/channels/{channel_id}/patch` - Patch channel

## Actions

- list: List channels (GET /api/v4/channels)
- create: Create channel (POST /api/v4/channels)
- get_by_id: Get channel (GET /api/v4/channels/{channel_id})
- delete: Delete channel (DELETE /api/v4/channels/{channel_id})
- create_post: Create post (POST /api/v4/posts)
- list_posts: List posts (GET /api/v4/channels/{channel_id}/posts)
- list_teams: List teams (GET /api/v4/teams)
- list_users: List users (GET /api/v4/users)
- update: Update channel (PUT /api/v4/channels/{channel_id})
- patch: Patch channel (PATCH /api/v4/channels/{channel_id}/patch)

## Fields

- `display_name`: string [REQUIRED for create] — Display display name
- `name`: string [REQUIRED for create] — Display name
- `type`: string [REQUIRED for create] (O or P) — Resource type
- `team_id`: string [REQUIRED for create] — Team unique identifier
- `channel_id`: string [REQUIRED for create_post] — Channel unique identifier
- `message`: string [REQUIRED for create_post] — Message text

## Example Request Bodies

**Create Channel:**
```json
{"display_name": "Engineering Updates", "name": "engineering-updates", "type": "O", "team_id": "team-abc123"}
```

**Create Post:**
```json
{"channel_id": "chan-xyz789", "message": "Deployment to production completed successfully."}
```

## Response

**Channel object:**
- `id`: string — Unique channel identifier
- `name`: string — Channel name or title
- `status`: string — Current status
- `created_at`: string — Creation timestamp (ISO 8601)
- `updated_at`: string — Last update timestamp (ISO 8601)

## Error Responses

| Status | Meaning |
|--------|---------|
| 400 | Invalid request body — check required fields and types |
| 401 | Authentication failed — verify API key or token is valid and not expired |
| 403 | Forbidden — insufficient permissions or scope for this action |
| 404 | Resource not found — check the ID or identifier |
| 409 | Conflict — resource already exists or concurrent modification |
| 429 | Rate limited — too many requests, retry after delay |
| 500 | Server error — retry or check service status page |
