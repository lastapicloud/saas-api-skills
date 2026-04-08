---
name: microsoft-teams
description: Send messages, manage teams, channels, and chats in Microsoft Teams.
  Use when the user mentions teams, microsoft teams, team, channel, chat, meeting.
version: 1.0.0
skill_type: external
base_url_env: MICROSOFT_TEAMS_BASE_URL
auth_env_var: MICROSOFT_TEAMS_ACCESS_TOKEN
auth_type: bearer
triggers:
  - teams
  - microsoft teams
  - team
  - channel
  - chat
  - meeting
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires MICROSOFT_TEAMS_BASE_URL and MICROSOFT_TEAMS_ACCESS_TOKEN
  environment variables.
---

# Microsoft-Teams

Send messages, manage teams, channels, and chats in Microsoft Teams. Use when the user mentions teams, microsoft teams, team, channel, chat, meeting.

## API Endpoints

- **GET** `/teams` - List joined teams
- **GET** `/teams/{team_id}/channels` - List team channels
- **POST** `/teams/{team_id}/channels` - Create a channel
- **POST** `/teams/{team_id}/channels/{channel_id}/messages` - Send a channel message
- **GET** `/teams/{team_id}/channels/{channel_id}/messages` - List channel messages
- **GET** `/chats` - List chats
- **POST** `/chats/{chat_id}/messages` - Send a chat message
- **GET** `/teams/{team_id}/members` - List team members
- **POST** `/teams/{team-id}/members`
- **DELETE** `/teams/{team-id}/members/{membership-id}`
- **PATCH** `/teams/{team-id}/members/{membership-id}`
- **PATCH** `/teams/{team-id}`
- **GET** `/places` - Get place
- **POST** `/places` - Add new entity to places
- **PATCH** `/places/{place-id}` - Update place

## Actions

- list: List joined teams (GET /teams)
- list_channels: List team channels (GET /teams/{team_id}/channels)
- create: Create a channel (POST /teams/{team_id}/channels)
- create_messages: Send a channel message (POST /teams/{team_id}/channels/{channel_id}/messages)
- list_messages: List channel messages (GET /teams/{team_id}/channels/{channel_id}/messages)
- list_chats: List chats (GET /chats)
- create_messages_2: Send a chat message (POST /chats/{chat_id}/messages)
- list_members: List team members (GET /teams/{team_id}/members)
- create_members: POST /teams/{team-id}/members (POST /teams/{team-id}/members)
- delete: DELETE /teams/{team-id}/members/{membership-id} (DELETE /teams/{team-id}/members/{membership-id})
- update: PATCH /teams/{team-id}/members/{membership-id} (PATCH /teams/{team-id}/members/{membership-id})
- update_teams: PATCH /teams/{team-id} (PATCH /teams/{team-id})
- list_places: Get place (GET /places)
- create_places: Add new entity to places (POST /places)
- update_places: Update place (PATCH /places/{place-id})

## Fields

- `team_id`: string [REQUIRED for team-scoped actions] (team ID)
- `channel_id`: string [REQUIRED for channel message actions] (channel ID)
- `chat_id`: string [REQUIRED for send_chat_message] (chat ID)
- `displayName`: string [REQUIRED for create_channel] (channel display name)
- `description`: string [OPTIONAL for create_channel] (channel description)
- `body`: object [REQUIRED for send messages] (message body with content and contentType)

## Example Request Bodies

**Send Channel Message:**
```json
{"body": {"content": "Hello from PythonREST!", "contentType": "text"}}
```

**Create Channel:**
```json
{"displayName": "Test Channel", "description": "A test channel"}
```
