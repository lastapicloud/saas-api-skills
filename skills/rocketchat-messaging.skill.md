---
name: rocketchat-messaging
description: Send messages and manage Rocket.Chat channels and users. Use when the
  user mentions rocket chat, rocketchat, message, channel, chat.
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
- list_channels_list: List channels (GET /api/v1/channels.list)
- create_channels_create: Create a channel (POST /api/v1/channels.create)
- create_channels_delete: Delete a channel (POST /api/v1/channels.delete)
- list_users_list: List users (GET /api/v1/users.list)
- list_users_info: Get user info (GET /api/v1/users.info)
- create_chat_delete: Delete a message (POST /api/v1/chat.delete)
- create_chat_update: Update a message (POST /api/v1/chat.update)
- list_me: Get current user (GET /api/v1/me)

## Fields

- `message`: object [REQUIRED for send] with `rid` (room ID), `msg` (text)
- `name`: string [REQUIRED for create channel]
- `members`: array of strings [OPTIONAL for create channel]

## Example Request Bodies

**Send Message:**
```json
{"message": {"rid": "GENERAL", "msg": "Hello team!"}}
```

**Create Channel:**
```json
{"name": "project-updates", "members": ["user1", "user2"]}
```
