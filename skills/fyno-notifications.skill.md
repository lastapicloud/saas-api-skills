---
name: fyno-notifications
description: Send multi-channel notifications via Fyno. Use when the user mentions
  fyno, notification, notify, push, sms, email, whatsapp.
version: 1.0.0
skill_type: external
base_url_env: FYNO_BASE_URL
auth_env_var: FYNO_API_KEY
auth_type: header
triggers:
  - fyno
  - notification
  - notify
  - push
  - sms
  - email
  - whatsapp
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires FYNO_BASE_URL and FYNO_API_KEY environment variables.
---

# Fyno-Notifications

Send multi-channel notifications via Fyno. Use when the user mentions fyno, notification, notify, push, sms, email, whatsapp.

## API Endpoints

- **POST** `/v1/notifications` - Send notification
- **GET** `/v1/notifications` - List notifications
- **GET** `/v1/notifications/{id}` - Get notification
- **GET** `/v1/templates` - List templates
- **POST** `/v1/templates` - Create template
- **GET** `/v1/events` - List events
- **POST** `/v1/events` - Create event

## Actions

- create: Send notification (POST /v1/notifications)
- list: List notifications (GET /v1/notifications)
- get_by_id: Get notification (GET /v1/notifications/{id})
- list_templates: List templates (GET /v1/templates)
- create_templates: Create template (POST /v1/templates)
- list_events: List events (GET /v1/events)
- create_events: Create event (POST /v1/events)

## Fields

- `to`: object [REQUIRED for send]
- `event`: string [REQUIRED for send]
- `data`: object [OPTIONAL]

## Example Request Bodies

**Send Notification:**
```json
{"to": {"email": "user@example.com", "phone": "+1234567890"}, "event": "welcome_email", "data": {"username": "johndoe"}}
```

**Create Template:**
```json
{"event": "order_confirmation", "data": {"order_id": "ORD-12345", "total": "49.99"}}
```
