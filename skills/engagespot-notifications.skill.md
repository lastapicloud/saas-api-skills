---
name: engagespot-notifications
description: Send notifications via Engagespot. Use when the user mentions engagespot,
  notification, notify, in-app.
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
- create_profiles: Create profile (POST /v3/profiles)
- get_by_id_profiles: Get profile (GET /v3/profiles/{identifier})
- list_categories: List categories (GET /v3/categories)

## Fields

- `recipients`: array [REQUIRED for send]
- `notification`: object [REQUIRED for send]
- `category`: string [OPTIONAL]

## Example Request Bodies

**Send Notification:**
```json
{"recipients": ["user-12345"], "notification": {"title": "New message received", "message": "You have a new support ticket reply."}, "category": "support"}
```

**Create Profile:**
```json
{"identifier": "user-12345", "profile": {"name": "Jordan Lee", "email": "jordan@example.com"}}
```
