---
name: googlechat-messaging
description: Send messages and manage Google Chat spaces. Use when the user mentions
  google chat, gchat, space, chat.
version: 1.0.0
skill_type: external
base_url_env: GOOGLE_CHAT_BASE_URL
auth_env_var: GOOGLE_CHAT_TOKEN
auth_type: bearer
triggers:
  - google chat
  - gchat
  - space
  - chat
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires GOOGLE_CHAT_BASE_URL and GOOGLE_CHAT_TOKEN environment variables.
---

# Googlechat-Messaging

Send messages and manage Google Chat spaces. Use when the user mentions google chat, gchat, space, chat.

## API Endpoints

- **POST** `/v1/spaces/{spaceId}/messages` - Send a message
- **GET** `/v1/spaces/{spaceId}/messages` - List messages
- **GET** `/v1/spaces/{spaceId}/messages/{messageId}` - Get a message
- **PUT** `/v1/spaces/{spaceId}/messages/{messageId}` - Update a message
- **DELETE** `/v1/spaces/{spaceId}/messages/{messageId}` - Delete a message
- **GET** `/v1/spaces` - List spaces
- **GET** `/v1/spaces/{spaceId}` - Get a space
- **POST** `/v1/spaces` - Create a space
- **GET** `/v1/spaces/{spaceId}/members` - List members

## Actions

- create: Send a message (POST /v1/spaces/{spaceId}/messages)
- list: List messages (GET /v1/spaces/{spaceId}/messages)
- get_by_id: Get a message (GET /v1/spaces/{spaceId}/messages/{messageId})
- update: Update a message (PUT /v1/spaces/{spaceId}/messages/{messageId})
- delete: Delete a message (DELETE /v1/spaces/{spaceId}/messages/{messageId})
- list_spaces: List spaces (GET /v1/spaces)
- get_by_id_spaces: Get a space (GET /v1/spaces/{spaceId})
- create_spaces: Create a space (POST /v1/spaces)
- list_members: List members (GET /v1/spaces/{spaceId}/members)

## Fields

- `text`: string [REQUIRED for send message]
- `cards`: array [OPTIONAL for rich messages]
- `displayName`: string [REQUIRED for create space]
- `spaceType`: string [REQUIRED for create space] ("SPACE" or "GROUP_CHAT")

## Example Request Bodies

**Send Message:**
```json
{"text": "Hello team! The deployment is complete."}
```

**Create Space:**
```json
{"displayName": "Project Alpha", "spaceType": "SPACE"}
```
