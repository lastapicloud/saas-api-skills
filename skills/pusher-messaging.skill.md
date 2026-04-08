---
name: pusher-messaging
description: Send real-time messages via Pusher Channels. Use when the user mentions
  pusher, realtime, channel, event, websocket, messaging.
version: 1.0.0
skill_type: external
base_url_env: PUSHER_BASE_URL
auth_env_var: PUSHER_API_KEY
auth_user_env: PUSHER_APP_SECRET
auth_type: header
triggers:
  - pusher
  - realtime
  - channel
  - event
  - websocket
  - messaging
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires PUSHER_BASE_URL and PUSHER_API_KEY environment variables.
---

# Pusher-Messaging

Send real-time messages via Pusher Channels. Use when the user mentions pusher, realtime, channel, event, websocket, messaging.

## API Endpoints

- **POST** `/apps/{appId}/events` - Trigger event
- **POST** `/apps/{appId}/batch_events` - Trigger batch events
- **GET** `/apps/{appId}/channels` - List channels
- **GET** `/apps/{appId}/channels/{channelName}` - Get channel info
- **GET** `/apps/{appId}/channels/{channelName}/users` - List channel users
- **POST** `/apps/{appId}/users/{userId}/terminate_connections` - Terminate user connections
- **PATCH** `/apps/{appId}/channels/{channelName}` - Update channel

## Actions

- create: Trigger event (POST /apps/{appId}/events)
- create_batch_events: Trigger batch events (POST /apps/{appId}/batch_events)
- list: List channels (GET /apps/{appId}/channels)
- get_by_id: Get channel info (GET /apps/{appId}/channels/{channelName})
- list_users: List channel users (GET /apps/{appId}/channels/{channelName}/users)
- create_terminate_connections: Terminate user connections (POST /apps/{appId}/users/{userId}/terminate_connections)
- update: Update channel (PATCH /apps/{appId}/channels/{channelName})

## Fields

- `name`: string [REQUIRED for trigger] (event name)
- `channels`: array [REQUIRED for trigger]
- `data`: string [REQUIRED for trigger]

## Example Request Bodies

**Trigger Event:**
```json
{"name": "new-message", "channels": ["chat-room-1"], "data": "{\"text\": \"Hello world\"}"}
```

**Trigger Batch Events:**
```json
{"batch": [{"name": "new-message", "channel": "chat-room-1", "data": "{\"text\": \"Hello\"}"}]}
