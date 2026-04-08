---
name: crisp-support
description: Manage Crisp conversations and contacts. Use when the user mentions crisp,
  conversation, message, chat, support.
version: 1.0.0
skill_type: external
base_url_env: CRISP_BASE_URL
auth_env_var: CRISP_TOKEN_SECRET
auth_user_env: CRISP_TOKEN_ID
auth_type: basic
triggers:
  - crisp
  - conversation
  - message
  - chat
  - support
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires CRISP_BASE_URL and CRISP_TOKEN_SECRET environment variables.
---

# Crisp-Support

Manage Crisp conversations and contacts. Use when the user mentions crisp, conversation, message, chat, support.

## API Endpoints

- **GET** `/v1/website/{websiteId}/conversations` - List conversations
- **GET** `/v1/website/{websiteId}/conversation/{sessionId}` - Get a conversation
- **POST** `/v1/website/{websiteId}/conversation` - Create a conversation
- **POST** `/v1/website/{websiteId}/conversation/{sessionId}/message` - Send a message
- **GET** `/v1/website/{websiteId}/conversation/{sessionId}/messages` - List messages
- **PATCH** `/v1/website/{websiteId}/conversation/{sessionId}/meta` - Update metadata
- **GET** `/v1/website/{websiteId}/people/profiles` - List people
- **GET** `/v1/website/{websiteId}/people/profile/{peopleId}` - Get a person
- **GET** `/v1/website/{websiteId}/operators/list` - List operators

## Actions

- list: List conversations (GET /v1/website/{websiteId}/conversations)
- get_by_id: Get a conversation (GET /v1/website/{websiteId}/conversation/{sessionId})
- create: Create a conversation (POST /v1/website/{websiteId}/conversation)
- create_message: Send a message (POST /v1/website/{websiteId}/conversation/{sessionId}/message)
- list_messages: List messages (GET /v1/website/{websiteId}/conversation/{sessionId}/messages)
- patch_meta: Update metadata (PATCH /v1/website/{websiteId}/conversation/{sessionId}/meta)
- list_profiles: List people (GET /v1/website/{websiteId}/people/profiles)
- get_by_id_profile: Get a person (GET /v1/website/{websiteId}/people/profile/{peopleId})
- list_operators: List operators (GET /v1/website/{websiteId}/operators/list)

## Fields

- `type`: string [REQUIRED for send message] ("text")
- `content`: string [REQUIRED for send message]
- `from`: string [REQUIRED for send message] ("operator" or "user")
- `origin`: string [REQUIRED for send message] ("chat")

## Example Request Bodies

**Send Message:**
```json
{"type": "text", "content": "Hello! How can I help you today?", "from": "operator", "origin": "chat"}
```

**Update Conversation Metadata:**
```json
{"nickname": "VIP Customer", "email": "vip@example.com", "segments": ["enterprise"]}
```
