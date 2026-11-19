---
name: rocketchat-messaging
description: 'Send messages and manage Rocket.Chat channels and users. Use when the
  user mentions rocket chat, rocketchat, message, channel, chat.

  '
version: 1.0.0
skill_type: external
base_url_env: ROCKETCHAT_BASE_URL
auth_env_var: ROCKETCHAT_AUTH_TOKEN
auth_type: header
triggers:
  - rocket chat
  - rocketchat
  - message
  - channel
  - chat
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires ROCKETCHAT_BASE_URL and ROCKETCHAT_AUTH_TOKEN environment
  variables.
annotations:
  readOnlyHint: false
  destructiveHint: false
  idempotentHint: false
---

# Rocketchat-Messaging

Send messages and manage Rocket.Chat channels and users. Use when the user mentions rocket chat, rocketchat, message, channel, chat.


## API Endpoints

- **POST** `/api/v1/chat.sendMessage` - Send a message
- **GET** `/api/v1/channels.history` - Get channel history
- **GET** `/api/v1/channels.list` - List channels
- **POST** `/api/v1/channels.create` - Create a channel
- **POST** `/api/v1/channels.delete` - Delete a channel
- **GET** `/api/v1/users.list` - List users
- **GET** `/api/v1/users.info` - Get user info
- **POST** `/api/v1/chat.delete` - Delete a message
- **POST** `/api/v1/chat.update` - Update a message
- **GET** `/api/v1/me` - Get current user

## Actions

- create: Send a message (POST /api/v1/chat.sendMessage)
- list: Get channel history (GET /api/v1/channels.history)
- list_channels: List channels (GET /api/v1/channels.list)
- create_channel: Create a channel (POST /api/v1/channels.create)
- delete_channel: Delete a channel (POST /api/v1/channels.delete)
- list_users: List users (GET /api/v1/users.list)
- get_user_info: Get user info (GET /api/v1/users.info)
- delete_message: Delete a message (POST /api/v1/chat.delete)
- update_message: Update a message (POST /api/v1/chat.update)
- get_current_user: Get current user (GET /api/v1/me)

## Fields

- `message`: object [REQUIRED for send] with `rid` (room ID), `msg` (text) — Message text
- `name`: string [REQUIRED for create channel] — Display name
- `members`: array of strings [OPTIONAL for create channel] — List of members

## Example Request Bodies

**Send Message:**
```json
{"message": {"rid": "GENERAL", "msg": "Hello team!"}}
```

**Create Channel:**
```json
{"name": "project-updates", "members": ["user1", "user2"]}
```

## Response

**Chat.Sendmessage object:**
- `id`: string — Unique chat.sendmessage identifier
- `name`: string — Chat.Sendmessage name or title
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
