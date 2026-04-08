---
name: discord-messaging
description: "Complete Discord bot integration \u2014 guilds, channels, messages,\
  \ members, roles, webhooks, emojis, invites, threads, and user management. Use when\
  \ the user mentions discord, guild, server, channel, message, DM, bot, role, webhook,\
  \ emoji, invite, thread, member, ban."
version: 1.0.0
skill_type: external
base_url_env: DISCORD_BASE_URL
auth_env_var: DISCORD_BOT_TOKEN
auth_type: bearer
triggers:
  - discord
  - guild
  - server
  - channel
  - message
  - DM
  - bot
  - role
license: Apache-2.0
metadata:
  author: lastapi
  version: 2.0.0
compatibility: Requires DISCORD_BASE_URL and DISCORD_BOT_TOKEN environment variables.
---

# Discord-Messaging

Complete Discord bot integration — guilds, channels, messages, members, roles, webhooks, emojis, invites, threads, and user management. Use when the user mentions discord, guild, server, channel, message, DM, bot, role, webhook, emoji, invite, thread, member, ban.

## API Endpoints

- **GET** `/guilds/{guild_id}` - Get a guild
- **PATCH** `/guilds/{guild_id}` - Modify a guild
- **GET** `/guilds/{guild_id}/channels` - List guild channels
- **POST** `/guilds/{guild_id}/channels` - Create a guild channel
- **GET** `/guilds/{guild_id}/members/{user_id}` - Get a guild member
- **GET** `/guilds/{guild_id}/members` - List guild members
- **GET** `/guilds/{guild_id}/members/search` - Search guild members
- **PUT** `/guilds/{guild_id}/members/{user_id}` - Add a guild member
- **DELETE** `/guilds/{guild_id}/members/{user_id}` - Remove a guild member
- **PUT** `/guilds/{guild_id}/bans/{user_id}` - Ban a user
- **DELETE** `/guilds/{guild_id}/bans/{user_id}` - Unban a user
- **GET** `/guilds/{guild_id}/bans` - List guild bans
- **GET** `/guilds/{guild_id}/roles` - Get guild roles
- **POST** `/guilds/{guild_id}/roles` - Create a guild role
- **PATCH** `/guilds/{guild_id}/roles/{role_id}` - Modify a guild role

## Actions

- get_by_id: Get a guild (GET /guilds/{guild_id})
- update: Modify a guild (PATCH /guilds/{guild_id})
- list: List guild channels (GET /guilds/{guild_id}/channels)
- create: Create a guild channel (POST /guilds/{guild_id}/channels)
- get_by_id_members: Get a guild member (GET /guilds/{guild_id}/members/{user_id})
- list_members: List guild members (GET /guilds/{guild_id}/members)
- search: Search guild members (GET /guilds/{guild_id}/members/search)
- update_members: Add a guild member (PUT /guilds/{guild_id}/members/{user_id})
- delete: Remove a guild member (DELETE /guilds/{guild_id}/members/{user_id})
- update_bans: Ban a user (PUT /guilds/{guild_id}/bans/{user_id})
- delete_bans: Unban a user (DELETE /guilds/{guild_id}/bans/{user_id})
- list_bans: List guild bans (GET /guilds/{guild_id}/bans)
- list_roles: Get guild roles (GET /guilds/{guild_id}/roles)
- create_roles: Create a guild role (POST /guilds/{guild_id}/roles)
- update_roles: Modify a guild role (PATCH /guilds/{guild_id}/roles/{role_id})

## Fields

### Message
- `content`: string [REQUIRED unless embeds/components/files provided] - Message text content (max 2000 characters)
- `embeds`: array [OPTIONAL] - Array of embed objects for rich content (max 10 per message)
- `components`: array [OPTIONAL] - Array of Action Row objects containing buttons/select menus
- `tts`: boolean [OPTIONAL] - Whether this is a text-to-speech message (default false)
- `message_reference`: object [OPTIONAL] - Reference to reply to a message: {message_id, channel_id, guild_id}
- `allowed_mentions`: object [OPTIONAL] - Control mention behavior: {parse, roles, users, replied_user}
- `flags`: integer [OPTIONAL] - Message flags bitfield (e.g., 4 = SUPPRESS_EMBEDS, 4096 = SUPPRESS_NOTIFICATIONS)
- `sticker_ids`: array [OPTIONAL] - Array of sticker snowflake IDs (max 3)

### Channel
- `name`: string [REQUIRED for create] - Channel name (1-100 chars, lowercase, no spaces for text channels)
- `type`: integer [REQUIRED for create] - Channel type (0=text, 2=voice, 4=category, 5=announcement, 13=stage, 15=forum, 16=media)
- `topic`: string [OPTIONAL] - Channel topic (max 1024 chars for text, 4096 for forum)
- `bitrate`: integer [OPTIONAL] - Voice channel bitrate (8000-384000 bps)
- `user_limit`: integer [OPTIONAL] - Voice channel user limit (0=unlimited, max 99; 10000 for stage)
- `rate_limit_per_user`: integer [OPTIONAL] - Slowmode in seconds (0-21600)
- `position`: integer [OPTIONAL] - Sorting position in channel list
- `permission_overwrites`: array [OPTIONAL] - Array of overwrite objects: {id, type (0=role, 1=member), allow, deny}
- `parent_id`: string [OPTIONAL] - Parent category snowflake ID
- `nsfw`: boolean [OPTIONAL] - Whether the channel is NSFW (default false)
- `default_auto_archive_duration`: integer [OPTIONAL] - Thread auto-archive duration in minutes (60, 1440, 4320, 10080)

### Guild
- `name`: string [REQUIRED for modify] - Guild name (2-100 chars)
- `description`: string [OPTIONAL] - Guild description (max 120 chars, requires COMMUNITY feature)
- `icon`: string [OPTIONAL] - Base64-encoded image data for guild icon
- `verification_level`: integer [OPTIONAL] - 0=none, 1=low (email), 2=medium (5 min), 3=high (10 min), 4=very high (phone)
- `default_message_notifications`: integer [OPTIONAL] - 0=all messages, 1=only mentions
- `explicit_content_filter`: integer [OPTIONAL] - 0=disabled, 1=members without roles, 2=all members
- `afk_channel_id`: string [OPTIONAL] - AFK voice channel snowflake ID
- `afk_timeout`: integer [OPTIONAL] - AFK timeout in seconds (60, 300, 900, 1800, 3600)
- `system_channel_id`: string [OPTIONAL] - System message channel snowflake ID

### Role
- `name`: string [REQUIRED for create] - Role name (max 100 chars)
- `permissions`: string [OPTIONAL] - Permission bitfield as string (use bitwise OR to combine, e.g., "2048" for SEND_MESSAGES)
- `color`: integer [OPTIONAL] - RGB color value as integer (e.g., 0xFF0000 for red, 3447003 for blue)
- `hoist`: boolean [OPTIONAL] - Whether to display role separately in member list (default false)
- `mentionable`: boolean [OPTIONAL] - Whether the role can be mentioned by everyone (default false)
- `icon`: string [OPTIONAL] - Base64-encoded image for role icon (requires ROLE_ICONS feature)
- `unicode_emoji`: string [OPTIONAL] - Unicode emoji for role icon (requires ROLE_ICONS feature)

### Webhook
- `name`: string [REQUIRED for create] - Webhook name (1-80 chars)
- `avatar`: string [OPTIONAL] - Base64-encoded image for webhook avatar
- `channel_id`: string [OPTIONAL for modify] - Move webhook to a different channel

### Emoji
- `name`: string [REQUIRED for create] - Emoji name (2-32 chars, alphanumeric and underscores)
- `image`: string [REQUIRED for create] - Base64-encoded image data (max 256KB, 128x128 recommended)
- `roles`: array [OPTIONAL] - Array of role snowflake IDs that can use this emoji

### Invite
- `max_age`: integer [OPTIONAL] - Duration in seconds before expiry (0=never, default 86400)
- `max_uses`: integer [OPTIONAL] - Max number of uses (0=unlimited, default 0)
- `temporary`: boolean [OPTIONAL] - Whether to grant temporary membership (default false)
- `unique`: boolean [OPTIONAL] - Whether to create a new unique invite (default false)

### Prune
- `days`: integer [REQUIRED] - Number of days of inactivity (1-30)
- `compute_prune_count`: boolean [OPTIONAL] - Whether to return the prune count (default true, disable for large guilds)
- `include_roles`: array [OPTIONAL] - Array of role snowflake IDs to include in prune

### Thread
- `name`: string [REQUIRED] - Thread name (1-100 chars)
- `auto_archive_duration`: integer [OPTIONAL] - Minutes of inactivity before auto-archiving (60, 1440, 4320, 10080)
- `rate_limit_per_user`: integer [OPTIONAL] - Slowmode in seconds (0-21600)

## Example Requests

**Send a Text Message:**
```json
{
  "content": "Hello from PythonREST!"
}
```

**Send a Message with Embed:**
```json
{
  "content": "Check out this update:",
  "embeds": [
    {
      "title": "Deployment Complete",
      "description": "Version 2.0.0 has been deployed to production.",
      "color": 3066993,
      "fields": [
        {"name": "Environment", "value": "Production", "inline": true},
        {"name": "Status", "value": "Healthy", "inline": true},
        {"name": "Deploy Time", "value": "2m 34s", "inline": true}
      ],
      "footer": {"text": "Deployed by CI/CD Pipeline"},
      "timestamp": "2026-03-25T12:00:00.000Z"
    }
  ]
}
```

**Send a Message with Button Components:**
```json
{
  "content": "Please confirm your action:",
  "components": [
    {
      "type": 1,
      "components": [
        {"type": 2, "style": 3, "label": "Approve", "custom_id": "approve_btn"},
        {"type": 2, "style": 4, "label": "Reject", "custom_id": "reject_btn"},
        {"type": 2, "style": 5, "label": "View Docs", "url": "https://example.com/docs"}
      ]
    }
  ]
}
```

**Create a Text Channel:**
```json
{
  "name": "announcements",
  "type": 0,
  "topic": "Important announcements and updates",
  "rate_limit_per_user": 10,
  "permission_overwrites": [
    {
      "id": "123456789012345678",
      "type": 0,
      "deny": "2048"
    }
  ]
}
```

**Create a Voice Channel:**
```json
{
  "name": "Team Voice",
  "type": 2,
  "bitrate": 96000,
  "user_limit": 10,
  "parent_id": "123456789012345678"
}
```

**Create a Role:**
```json
{
  "name": "Moderator",
  "permissions": "1099511627775",
  "color": 3447003,
  "hoist": true,
  "mentionable": true
}
```

**Assign a Role to a Member (Add Guild Member Role):**
```
PUT /guilds/{guild_id}/members/{user_id}/roles/{role_id}
(empty body)
```

**Ban a User:**
```json
{
  "delete_message_seconds": 86400
}
```

**Create a Webhook:**
```json
{
  "name": "Deploy Notifications",
  "avatar": null
}
```

**Execute a Webhook:**
```json
{
  "content": "New deployment started",
  "username": "CI Bot",
  "avatar_url": "https://example.com/bot-avatar.png",
  "embeds": [
    {
      "title": "Build #1234",
      "description": "Building branch `main` at commit `abc1234`",
      "color": 16776960
    }
  ]
}
```

**Create a Channel Invite:**
```json
{
  "max_age": 3600,
  "max_uses": 10,
  "temporary": false,
  "unique": true
}
```

**Bulk Delete Messages:**
```json
{
  "messages": ["111111111111111111", "222222222222222222", "333333333333333333"]
}
```

**Create a Thread from Message:**
```json
{
  "name": "Discussion Thread",
  "auto_archive_duration": 1440
}
```

**Create a Guild Emoji:**
```json
{
  "name": "custom_emoji",
  "image": "data:image/png;base64,iVBORw0KGgo...",
  "roles": []
}
```

**Begin Guild Prune (remove inactive members):**
```json
{
  "days": 7,
  "compute_prune_count": true,
  "include_roles": ["123456789012345678"]
}
```

**Get Messages (Query Parameters):**
```
GET /channels/{channel_id}/messages?limit=50&before=123456789012345678
```

**List Guild Members (Query Parameters):**
```
GET /guilds/{guild_id}/members?limit=100&after=123456789012345678
```

**Search Guild Members (Query Parameters):**
```
GET /guilds/{guild_id}/members/search?query=john&limit=10
```
