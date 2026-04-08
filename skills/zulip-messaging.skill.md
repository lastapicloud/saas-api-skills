---
name: zulip-messaging
description: Send messages and manage Zulip streams and topics. Use when the user
  mentions zulip, message, stream, topic, chat.
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
- create_subscriptions: Subscribe to streams (POST /api/v1/users/me/subscriptions)
- list_users: List users (GET /api/v1/users)
- list_me: Get current user (GET /api/v1/users/me)
- create_reactions: Add reaction (POST /api/v1/messages/{messageId}/reactions)
- list_subscriptions: Get subscriptions (GET /api/v1/users/{userId}/subscriptions)

## Fields

- `type`: string [REQUIRED for send] ("stream" or "private")
- `to`: string or array [REQUIRED for send] (stream name or user IDs)
- `topic`: string [REQUIRED for stream message]
- `content`: string [REQUIRED for send]

## Example Request Bodies

**Send Stream Message:**
```json
{"type": "stream", "to": "engineering", "topic": "deployments", "content": "Deployed v2.1.0 to production."}
```

**Send Private Message:**
```json
{"type": "private", "to": [12345], "content": "Can you review my PR?"}
```
