---
name: engagespot-notifications
description: 'Send notifications via Engagespot. Use when the user mentions engagespot,
  notification, notify, in-app.

  '
version: 1.0.0
skill_type: external
base_url_env: ENGAGESPOT_BASE_URL
auth_env_var: ENGAGESPOT_API_KEY
auth_type: header
triggers:
  - engagespot
  - notification
  - notify
  - in-app
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires ENGAGESPOT_BASE_URL and ENGAGESPOT_API_KEY environment variables.
annotations:
  readOnlyHint: false
  destructiveHint: true
  idempotentHint: false
---

# Engagespot-Notifications

Send notifications via Engagespot. Use when the user mentions engagespot, notification, notify, in-app.


## API Endpoints

- **POST** `/v3/notifications` - Send notification
- **GET** `/v3/notifications` - List notifications
- **GET** `/v3/notifications/{id}` - Get notification
- **DELETE** `/v3/notifications/{id}` - Delete notification
- **POST** `/v3/profiles` - Create profile
- **GET** `/v3/profiles/{identifier}` - Get profile
- **GET** `/v3/categories` - List categories

## Actions

- create: Send notification (POST /v3/notifications)
- list: List notifications (GET /v3/notifications)
- get_by_id: Get notification (GET /v3/notifications/{id})
- delete: Delete notification (DELETE /v3/notifications/{id})
- create_profile: Create profile (POST /v3/profiles)
- get_profile: Get profile (GET /v3/profiles/{identifier})
- list_categories: List categories (GET /v3/categories)

## Fields

- `recipients`: array [REQUIRED for send] — List of recipients
- `notification`: object [REQUIRED for send] — Notification configuration
- `category`: string [OPTIONAL] — Category

## Example Request Bodies

**Send Notification:**
```json
{"recipients": ["user-12345"], "notification": {"title": "New message received", "message": "You have a new support ticket reply."}, "category": "support"}
```

**Create Profile:**
```json
{"identifier": "user-12345", "profile": {"name": "Jordan Lee", "email": "jordan@example.com"}}
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
