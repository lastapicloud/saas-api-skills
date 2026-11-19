---
name: zulip-messaging
description: 'Send messages and manage Zulip streams and topics. Use when the user
  mentions zulip, message, stream, topic, chat.

  '
version: 1.0.0
skill_type: external
base_url_env: ZULIP_BASE_URL
auth_env_var: ZULIP_API_KEY
auth_user_env: ZULIP_EMAIL
auth_type: basic
triggers:
  - zulip
  - message
  - stream
  - topic
  - chat
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires ZULIP_BASE_URL and ZULIP_API_KEY environment variables.
annotations:
  readOnlyHint: false
  destructiveHint: true
  idempotentHint: false
---

# Zulip-Messaging

Send messages and manage Zulip streams and topics. Use when the user mentions zulip, message, stream, topic, chat.


## API Endpoints

- **POST** `/api/v1/messages` - Send a message
- **GET** `/api/v1/messages` - Get messages
- **PATCH** `/api/v1/messages/{messageId}` - Edit a message
- **DELETE** `/api/v1/messages/{messageId}` - Delete a message
- **GET** `/api/v1/streams` - List streams
- **POST** `/api/v1/users/me/subscriptions` - Subscribe to streams
- **GET** `/api/v1/users` - List users
- **GET** `/api/v1/users/me` - Get current user
- **POST** `/api/v1/messages/{messageId}/reactions` - Add reaction
- **GET** `/api/v1/users/{userId}/subscriptions` - Get subscriptions

## Actions

- create: Send a message (POST /api/v1/messages)
- list: Get messages (GET /api/v1/messages)
- update: Edit a message (PATCH /api/v1/messages/{messageId})
- delete: Delete a message (DELETE /api/v1/messages/{messageId})
- list_streams: List streams (GET /api/v1/streams)
- create_subscribe_streams: Subscribe to streams (POST /api/v1/users/me/subscriptions)
- list_users: List users (GET /api/v1/users)
- get_current_user: Get current user (GET /api/v1/users/me)
- add_reaction: Add reaction (POST /api/v1/messages/{messageId}/reactions)
- get_subscriptions: Get subscriptions (GET /api/v1/users/{userId}/subscriptions)

## Fields

- `type`: string [REQUIRED for send] ("stream" or "private") — Resource type
- `to`: string or array [REQUIRED for send] (stream name or user IDs) — To
- `topic`: string [REQUIRED for stream message] — Topic
- `content`: string [REQUIRED for send] — Content body

## Example Request Bodies

**Send Stream Message:**
```json
{"type": "stream", "to": "engineering", "topic": "deployments", "content": "Deployed v2.1.0 to production."}
```

**Send Private Message:**
```json
{"type": "private", "to": [12345], "content": "Can you review my PR?"}
```

## Response

**Message object:**
- `id`: string — Unique message identifier
- `name`: string — Message name or title
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
