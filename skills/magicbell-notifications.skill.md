---
name: magicbell-notifications
description: Send and manage notifications via MagicBell. Use when the user mentions
  magicbell, notification, notify, inbox, bell.
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
- create_read: Mark as read (POST /notifications/{id}/read)
- create_unread: Mark as unread (POST /notifications/{id}/unread)
- list_notification_preferences: Get preferences (GET /notification_preferences)

## Fields

- `title`: string [REQUIRED for create]
- `recipients`: array [REQUIRED for create]
- `content`: string [OPTIONAL]
- `action_url`: string [OPTIONAL]

## Example Request Bodies

**Create Notification:**
```json
{"title": "New comment on your post", "recipients": [{"email": "user@example.com"}], "content": "Someone commented on your blog post.", "action_url": "https://app.example.com/posts/123"}
```

**Mark as Read:**
```json
{}
```
