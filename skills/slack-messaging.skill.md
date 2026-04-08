---
name: slack-messaging
description: "Complete Slack workspace management \u2014 messages, conversations,\
  \ users, files, reactions, search, bookmarks, reminders, and app permissions. Use\
  \ when the user mentions slack, message, channel, DM, notify, chat, send message,\
  \ thread, conversation, reaction, file, reminder, bookmark."
version: 1.0.0
skill_type: external
base_url_env: SLACK_BASE_URL
auth_env_var: SLACK_BOT_TOKEN
auth_type: bearer
triggers:
  - slack
  - message
  - channel
  - DM
  - notify
  - chat
  - send message
  - thread
license: Apache-2.0
metadata:
  author: lastapi
  version: 2.0.0
compatibility: Requires SLACK_BASE_URL and SLACK_BOT_TOKEN environment variables.
---

# Slack-Messaging

Complete Slack workspace management — messages, conversations, users, files, reactions, search, bookmarks, reminders, and app permissions. Use when the user mentions slack, message, channel, DM, notify, chat, send message, thread, conversation, reaction, file, reminder, bookmark.

## API Endpoints

- **POST** `/chat.postMessage` - Send a message to a channel
- **POST** `/chat.update` - Update an existing message
- **POST** `/chat.delete` - Delete a message
- **POST** `/chat.scheduleMessage` - Schedule a message for future delivery
- **POST** `/pins.add` - Pin a message to a channel
- **POST** `/pins.remove` - Unpin a message from a channel
- **POST** `/conversations.create` - Create a new channel
- **GET** `/conversations.list` - List all channels in a workspace
- **GET** `/conversations.info` - Get info about a channel
- **POST** `/conversations.join` - Join an existing channel
- **POST** `/conversations.leave` - Leave a channel
- **POST** `/conversations.archive` - Archive a channel
- **POST** `/conversations.invite` - Invite users to a channel
- **POST** `/conversations.kick` - Remove a user from a channel
- **POST** `/conversations.rename` - Rename a channel

## Actions

- create: Send a message to a channel (POST /chat.postMessage)
- create_chat_update: Update an existing message (POST /chat.update)
- create_chat_delete: Delete a message (POST /chat.delete)
- create_chat_schedulemessage: Schedule a message for future delivery (POST /chat.scheduleMessage)
- create_pins_add: Pin a message to a channel (POST /pins.add)
- create_pins_remove: Unpin a message from a channel (POST /pins.remove)
- create_conversations_create: Create a new channel (POST /conversations.create)
- list: List all channels in a workspace (GET /conversations.list)
- list_conversations_info: Get info about a channel (GET /conversations.info)
- create_conversations_join: Join an existing channel (POST /conversations.join)
- create_conversations_leave: Leave a channel (POST /conversations.leave)
- create_conversations_archive: Archive a channel (POST /conversations.archive)
- create_conversations_invite: Invite users to a channel (POST /conversations.invite)
- create_conversations_kick: Remove a user from a channel (POST /conversations.kick)
- create_conversations_rename: Rename a channel (POST /conversations.rename)

## Fields

### Message (chat.postMessage / chat.update)
- `channel`: string [REQUIRED] - Channel ID (e.g., "C01ABCDEF"), private group ID, or DM ID
- `text`: string [REQUIRED] - Message text content. Required even when using blocks (serves as fallback for notifications)
- `thread_ts`: string [OPTIONAL] - Timestamp of parent message to reply in thread (e.g., "1234567890.123456")
- `reply_broadcast`: boolean [OPTIONAL] - When replying in a thread, also post to the channel (default false)
- `blocks`: array [OPTIONAL] - Block Kit layout blocks for rich formatting (JSON array of block objects)
- `attachments`: array [OPTIONAL] - Legacy secondary attachments (prefer blocks)
- `unfurl_links`: boolean [OPTIONAL] - Enable URL unfurling (default true)
- `unfurl_media`: boolean [OPTIONAL] - Enable media unfurling (default true)
- `mrkdwn`: boolean [OPTIONAL] - Enable markdown parsing (default true)
- `metadata`: object [OPTIONAL] - Message metadata (event_type + event_payload)
- `ts`: string [REQUIRED for update/delete] - Timestamp of the message to update or delete

### Scheduled Message (chat.scheduleMessage)
- `channel`: string [REQUIRED] - Channel ID to send the scheduled message to
- `text`: string [REQUIRED] - Message text content
- `post_at`: integer [REQUIRED] - Unix timestamp for when to send the message (max 120 days in the future)
- `thread_ts`: string [OPTIONAL] - Timestamp of parent message to reply in thread
- `blocks`: array [OPTIONAL] - Block Kit layout blocks
- `unfurl_links`: boolean [OPTIONAL] - Enable URL unfurling
- `unfurl_media`: boolean [OPTIONAL] - Enable media unfurling
- `metadata`: object [OPTIONAL] - Message metadata

### Conversation (conversations.create)
- `name`: string [REQUIRED] - Channel name (lowercase, no spaces, max 80 chars, hyphens and underscores allowed)
- `is_private`: boolean [OPTIONAL] - Create as private channel (default false)
- `team_id`: string [OPTIONAL] - Workspace ID for Enterprise Grid (required for cross-workspace channels)

### Conversation Actions
- `channel`: string [REQUIRED for join/leave/archive/invite/kick/rename/setTopic/setPurpose/history] - Channel ID
- `users`: string [REQUIRED for invite] - Comma-separated list of user IDs to invite
- `user`: string [REQUIRED for kick] - User ID to remove from channel
- `name`: string [REQUIRED for rename] - New channel name
- `topic`: string [REQUIRED for setTopic] - New channel topic (max 250 chars)
- `purpose`: string [REQUIRED for setPurpose] - New channel purpose (max 250 chars)
- `cursor`: string [OPTIONAL] - Pagination cursor from previous response
- `limit`: integer [OPTIONAL] - Number of results per page (1-1000, default 100)
- `latest`: string [OPTIONAL for history] - End of time range (message timestamp, default now)
- `oldest`: string [OPTIONAL for history] - Start of time range (message timestamp, default 0)
- `inclusive`: boolean [OPTIONAL for history] - Include messages with oldest or latest timestamps

### Conversations List Filters
- `types`: string [OPTIONAL] - Comma-separated channel types: public_channel, private_channel, mpim, im (default "public_channel")
- `exclude_archived`: boolean [OPTIONAL] - Exclude archived channels (default false)
- `team_id`: string [OPTIONAL] - Workspace ID for Enterprise Grid

### User
- `user`: string [REQUIRED for users.info / users.profile.get] - User ID (e.g., "U01ABCDEF")
- `include_locale`: boolean [OPTIONAL for users.info] - Include locale data

### File (files.uploadV2)
- `channel_id`: string [OPTIONAL] - Channel ID to share the file in
- `content`: string [CONDITIONAL] - File content as string (provide either content or file)
- `file`: binary [CONDITIONAL] - File data as multipart form upload (provide either content or file)
- `filename`: string [REQUIRED] - Name of the file
- `title`: string [OPTIONAL] - Title of the file
- `initial_comment`: string [OPTIONAL] - Message text to accompany the file
- `thread_ts`: string [OPTIONAL] - Thread timestamp to upload as a thread reply
- `filetype`: string [OPTIONAL] - File type identifier (e.g., "pdf", "png", "csv")
- `snippet_type`: string [OPTIONAL] - Syntax highlighting for text snippets (e.g., "python", "javascript")

### File Actions
- `file`: string [REQUIRED for delete/share] - File ID (e.g., "F01ABCDEF")
- `channel`: string [OPTIONAL for list] - Filter files by channel
- `user`: string [OPTIONAL for list] - Filter files by user
- `types`: string [OPTIONAL for list] - Filter by file type: all, spaces, snippets, images, gdocs, zips, pdfs
- `count`: integer [OPTIONAL for list] - Number of items per page (1-1000, default 100)
- `page`: integer [OPTIONAL for list] - Page number (default 1)
- `ts_from`: string [OPTIONAL for list] - Filter files created after this timestamp
- `ts_to`: string [OPTIONAL for list] - Filter files created before this timestamp

### Reaction
- `channel`: string [REQUIRED for add/remove] - Channel ID where the message is
- `name`: string [REQUIRED for add/remove] - Emoji name without colons (e.g., "thumbsup", not ":thumbsup:")
- `timestamp`: string [REQUIRED for add/remove] - Message timestamp to react to
- `user`: string [OPTIONAL for list] - User ID to list reactions for (defaults to authenticated user)
- `full`: boolean [OPTIONAL for list] - Include complete reaction list for each item

### Search
- `query`: string [REQUIRED] - Search query text (supports Slack search modifiers: from:, in:, has:, before:, after:, on:)
- `sort`: string [OPTIONAL] - Sort order: score (relevance) or timestamp (default score)
- `sort_dir`: string [OPTIONAL] - Sort direction: asc or desc (default desc)
- `count`: integer [OPTIONAL] - Number of results per page (1-100, default 20)
- `page`: integer [OPTIONAL] - Page number (default 1)
- `highlight`: boolean [OPTIONAL] - Include highlighted match snippets (default false)

### Bookmark
- `channel_id`: string [REQUIRED] - Channel ID
- `title`: string [REQUIRED for add] - Bookmark title
- `type`: string [REQUIRED for add] - Bookmark type: "link"
- `link`: string [REQUIRED for add, type=link] - URL for the bookmark
- `emoji`: string [OPTIONAL for add] - Emoji to display with the bookmark

### Reminder
- `text`: string [REQUIRED for add] - Reminder text
- `time`: string [REQUIRED for add] - When to send the reminder (Unix timestamp, or natural language like "in 15 minutes", "tomorrow at 9am")
- `user`: string [OPTIONAL for add] - User ID to create the reminder for (defaults to authenticated user)
- `reminder`: string [REQUIRED for delete] - Reminder ID to delete

### Pin
- `channel`: string [REQUIRED] - Channel ID
- `timestamp`: string [REQUIRED] - Message timestamp to pin or unpin

## Example Requests

**Post a Message:**
```json
{"channel": "C01ABCDEF", "text": "Hello from PythonREST!", "mrkdwn": true}
```

**Post a Threaded Reply:**
```json
{"channel": "C01ABCDEF", "text": "This is a reply in a thread", "thread_ts": "1234567890.123456", "reply_broadcast": false}
```

**Post a Message with Block Kit:**
```json
{
  "channel": "C01ABCDEF",
  "text": "New deployment completed",
  "blocks": [
    {"type": "header", "text": {"type": "plain_text", "text": "Deployment Complete"}},
    {"type": "section", "text": {"type": "mrkdwn", "text": "*Service:* api-gateway\n*Version:* v2.4.1\n*Status:* :white_check_mark: Success"}},
    {"type": "divider"},
    {"type": "context", "elements": [{"type": "mrkdwn", "text": "Deployed by <@U01ABCDEF> at <!date^1234567890^{date_short} {time}|2024-01-15>"}]}
  ]
}
```

**Update a Message:**
```json
{"channel": "C01ABCDEF", "ts": "1234567890.123456", "text": "Updated message content"}
```

**Delete a Message:**
```json
{"channel": "C01ABCDEF", "ts": "1234567890.123456"}
```

**Schedule a Message (30 minutes from now):**
```json
{"channel": "C01ABCDEF", "text": "This is a scheduled reminder", "post_at": 1711400000}
```

**Create a Public Channel:**
```json
{"name": "project-alpha", "is_private": false}
```

**Create a Private Channel:**
```json
{"name": "team-secrets", "is_private": true}
```

**Invite Users to a Channel:**
```json
{"channel": "C01ABCDEF", "users": "U01ABCDEF,U02GHIJKL"}
```

**Set Channel Topic:**
```json
{"channel": "C01ABCDEF", "topic": "Sprint 42 planning and standup notes"}
```

**Upload a File (v2):**
```json
{"channel_id": "C01ABCDEF", "content": "print('Hello, World!')", "filename": "hello.py", "title": "Hello World Script", "initial_comment": "Here is the script we discussed", "snippet_type": "python"}
```

**Add a Reaction:**
```json
{"channel": "C01ABCDEF", "name": "thumbsup", "timestamp": "1234567890.123456"}
```

**Remove a Reaction:**
```json
{"channel": "C01ABCDEF", "name": "thumbsup", "timestamp": "1234567890.123456"}
```

**Search Messages (Query Params):**
Query parameter: `query=deployment+failed+in:%23production&sort=timestamp&sort_dir=desc&count=20`

**Search Files (Query Params):**
Query parameter: `query=quarterly+report+filetype:pdf&sort=timestamp&count=10`

**Add a Bookmark:**
```json
{"channel_id": "C01ABCDEF", "title": "Sprint Board", "type": "link", "link": "https://jira.example.com/board/42", "emoji": ":clipboard:"}
```

**Create a Reminder:**
```json
{"text": "Review pull request #123", "time": "in 30 minutes"}
```

**Pin a Message:**
```json
{"channel": "C01ABCDEF", "timestamp": "1234567890.123456"}
```

**List Channels (Query Params):**
Query parameter: `types=public_channel,private_channel&exclude_archived=true&limit=50`

**Get Channel History (Query Params):**
Query parameter: `channel=C01ABCDEF&limit=25&oldest=1700000000.000000`
