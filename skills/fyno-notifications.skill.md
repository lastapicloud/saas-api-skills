---
name: fyno-notifications
description: 'Send multi-channel notifications via Fyno. Use when the user mentions
  fyno, notification, notify, push, sms, email, whatsapp.

  '
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
annotations:
  readOnlyHint: false
  destructiveHint: false
  idempotentHint: false
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
- create_template: Create template (POST /v1/templates)
- list_events: List events (GET /v1/events)
- create_event: Create event (POST /v1/events)

## Fields

- `to`: object [REQUIRED for send] — To configuration
- `event`: string [REQUIRED for send] — Event
- `data`: object [OPTIONAL] — Request payload data

## Example Request Bodies

**Send Notification:**
```json
{"to": {"email": "user@example.com", "phone": "+1234567890"}, "event": "welcome_email", "data": {"username": "johndoe"}}
```

**Create Template:**
```json
{"event": "order_confirmation", "data": {"order_id": "ORD-12345", "total": "49.99"}}
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
