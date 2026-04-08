---
name: webhook-management
description: Register, list, and manage webhook subscriptions for API events. Use
  when the user mentions webhook, notification, subscribe, event, hook.
version: 1.0.0
skill_type: database
base_url_env: WEBHOOK_BASE_URL
auth_env_var: WEBHOOK_API_TOKEN
auth_type: header
triggers:
  - webhook
  - notification
  - subscribe
  - event
  - hook
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: ''
---

# Webhook-Management

Register, list, and manage webhook subscriptions for API events. Use when the user mentions webhook, notification, subscribe, event, hook.

## API Endpoints

- **POST** `/webhooks` - Register a new webhook
- **GET** `/webhooks` - List all webhooks
- **GET** `/webhooks/{webhook_id}` - Get a webhook by ID
- **PATCH** `/webhooks/{webhook_id}` - Update a webhook
- **DELETE** `/webhooks/{webhook_id}` - Delete a webhook
- **GET** `/webhooks/{webhook_id}/logs` - Get dispatch logs
- **POST** `/webhooks/test/{webhook_id}` - Send a test ping

## Actions

- create: Register a new webhook (POST /webhooks)
- list: List all webhooks (GET /webhooks)
- get_by_id: Get a webhook by ID (GET /webhooks/{webhook_id})
- update: Update a webhook (PATCH /webhooks/{webhook_id})
- delete: Delete a webhook (DELETE /webhooks/{webhook_id})
- list_logs: Get dispatch logs (GET /webhooks/{webhook_id}/logs)
- add_test: Send a test ping (POST /webhooks/test/{webhook_id})

## Fields

- `url`: string [REQUIRED for create] - Target URL for webhook delivery (must be http:// or https://)
- `events`: array of strings [REQUIRED for create] - Event patterns (e.g., "orders.created", "*.updated", "users.*", "*.*")
- `secret`: string [OPTIONAL] - HMAC-SHA256 secret for payload signing
- `description`: string [OPTIONAL] - Human-readable description
- `headers`: object [OPTIONAL] - Custom headers to include in webhook requests
- `is_active`: boolean [OPTIONAL, default: true] - Whether the webhook is active

## Example Requests

### Register a webhook
```json
{
  "url": "https://myapp.com/hook",
  "events": ["orders.created", "*.updated"],
  "secret": "my-secret",
  "description": "Notify on new orders"
}
```

### Disable a webhook
```json
{
  "is_active": false
}
```
