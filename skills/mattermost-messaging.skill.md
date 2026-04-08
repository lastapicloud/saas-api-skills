---
name: mattermost-messaging
description: Manage channels and messages via Mattermost. Use when the user mentions
  mattermost, channel, message, team, chat.
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
- create_posts: Create post (POST /api/v4/posts)
- list_posts: List posts (GET /api/v4/channels/{channel_id}/posts)
- list_teams: List teams (GET /api/v4/teams)
- list_users: List users (GET /api/v4/users)
- update: Update channel (PUT /api/v4/channels/{channel_id})
- patch_patch: Patch channel (PATCH /api/v4/channels/{channel_id}/patch)

## Fields

- `display_name`: string [REQUIRED for create]
- `name`: string [REQUIRED for create]
- `type`: string [REQUIRED for create] (O or P)
- `team_id`: string [REQUIRED for create]
- `channel_id`: string [REQUIRED for create_post]
- `message`: string [REQUIRED for create_post]

## Example Request Bodies

**Create Channel:**
```json
{"display_name": "Engineering Updates", "name": "engineering-updates", "type": "O", "team_id": "team-abc123"}
```

**Create Post:**
```json
{"channel_id": "chan-xyz789", "message": "Deployment to production completed successfully."}
```
