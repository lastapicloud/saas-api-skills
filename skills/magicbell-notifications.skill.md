---
name: magicbell-notifications
description: 'Send and manage notifications via MagicBell. Use when the user mentions
  magicbell, notification, notify, inbox, bell.

  '
version: 1.0.0
skill_type: external
base_url_env: MAGICBELL_BASE_URL
auth_env_var: MAGICBELL_API_KEY
auth_user_env: MAGICBELL_API_SECRET
auth_type: header
triggers:
  - magicbell
  - notification
  - notify
  - inbox
  - bell
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires MAGICBELL_BASE_URL and MAGICBELL_API_KEY environment variables.
annotations:
  readOnlyHint: false
  destructiveHint: true
  idempotentHint: false
---

# Magicbell-Notifications

Send and manage notifications via MagicBell. Use when the user mentions magicbell, notification, notify, inbox, bell.


## API Endpoints

- **POST** `/notifications` - Create notification
- **GET** `/notifications` - List notifications
- **GET** `/notifications/{id}` - Get notification
- **DELETE** `/notifications/{id}` - Delete notification
- **POST** `/notifications/{id}/read` - Mark as read
- **POST** `/notifications/{id}/unread` - Mark as unread
- **GET** `/notification_preferences` - Get preferences

## Actions

- create: Create notification (POST /notifications)
- list: List notifications (GET /notifications)
- get_by_id: Get notification (GET /notifications/{id})
- delete: Delete notification (DELETE /notifications/{id})
- create_mark_as_read: Mark as read (POST /notifications/{id}/read)
- create_mark_as_unread: Mark as unread (POST /notifications/{id}/unread)
- get_preferences: Get preferences (GET /notification_preferences)

## Fields

- `title`: string [REQUIRED for create] — Title or heading
- `recipients`: array [REQUIRED for create] — List of recipients
- `content`: string [OPTIONAL] — Content body
- `action_url`: string [OPTIONAL] — Action url

## Example Request Bodies

**Create Notification:**
```json
{"title": "New comment on your post", "recipients": [{"email": "user@example.com"}], "content": "Someone commented on your blog post.", "action_url": "https://app.example.com/posts/123"}
```

**Mark as Read:**
```json
{}
```

## Response

**Notification object:**
- `id`: string — Unique notification identifier
- `name`: string — Notification name or title
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
