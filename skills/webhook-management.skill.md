---
name: webhook-management
description: "Register, list, and manage webhook subscriptions for API events. Use\
  \ when the user mentions webhook, notification, subscribe, event, hook.\n (API 9.3.0)\
  \ (API v3)"
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
compatibility: Requires WEBHOOK_BASE_URL and WEBHOOK_API_TOKEN environment variables.
annotations:
  readOnlyHint: false
  destructiveHint: true
  idempotentHint: false
---

# Webhook-Management

Register, list, and manage webhook subscriptions for API events. Use when the user mentions webhook, notification, subscribe, event, hook.
 (API 9.3.0) (API v3)

## API Endpoints

- **PUT** `/webhooks/v3/{appId}/settings`
- **GET** `/webhooks/v3/{appId}/settings`
- **GET** `/webhooks/v3/{appId}/subscriptions`
- **PATCH** `/webhooks/v3/{appId}/subscriptions/{subscriptionId}`
- **GET** `/webhooks/v3/{appId}/subscriptions/{subscriptionId}`
- **DELETE** `/webhooks/v3/{appId}/settings`
- **DELETE** `/webhooks/v3/{appId}/subscriptions/{subscriptionId}`
- **POST** `/webhooks/v3/{appId}/subscriptions`
- **POST** `/webhooks/v3/{appId}/subscriptions/batch/update`
- **GET** `/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Automation/automationAccounts/{automationAccountName}/webhooks` - Retrieve a list of webhooks.
- **PUT** `/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Automation/automationAccounts/{automationAccountName}/webhooks/{webhookName}` - Create the webhook identified by webhook name.
- **GET** `/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Automation/automationAccounts/{automationAccountName}/webhooks/{webhookName}` - Retrieve the webhook identified by webhook name.
- **PATCH** `/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Automation/automationAccounts/{automationAccountName}/webhooks/{webhookName}` - Update the webhook identified by webhook name.
- **DELETE** `/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Automation/automationAccounts/{automationAccountName}/webhooks/{webhookName}` - Delete the webhook by name.
- **POST** `/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Automation/automationAccounts/{automationAccountName}/webhooks/generateUri` - Generates a Uri for use in creating a webhook.

## Actions

- put_settings: PUT /webhooks/v3/{appId}/settings (PUT /webhooks/v3/{appId}/settings)
- list: GET /webhooks/v3/{appId}/settings (GET /webhooks/v3/{appId}/settings)
- list_subscriptions: GET /webhooks/v3/{appId}/subscriptions (GET /webhooks/v3/{appId}/subscriptions)
- update: PATCH /webhooks/v3/{appId}/subscriptions/{subscriptionId} (PATCH /webhooks/v3/{appId}/subscriptions/{subscriptionId})
- get_by_id: GET /webhooks/v3/{appId}/subscriptions/{subscriptionId} (GET /webhooks/v3/{appId}/subscriptions/{subscriptionId})
- delete_settings: DELETE /webhooks/v3/{appId}/settings (DELETE /webhooks/v3/{appId}/settings)
- delete: DELETE /webhooks/v3/{appId}/subscriptions/{subscriptionId} (DELETE /webhooks/v3/{appId}/subscriptions/{subscriptionId})
- create: POST /webhooks/v3/{appId}/subscriptions (POST /webhooks/v3/{appId}/subscriptions)
- create_update: POST /webhooks/v3/{appId}/subscriptions/batch/update (POST /webhooks/v3/{appId}/subscriptions/batch/update)
- get_retrieve_list_webhooks: Retrieve a list of webhooks. (GET /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Automation/automationAccounts/{automationAccountName}/webhooks)
- create_webhook_identified_webhook: Create the webhook identified by webhook name. (PUT /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Automation/automationAccounts/{automationAccountName}/webhooks/{webhookName})
- get_retrieve_webhook_identified_webhook: Retrieve the webhook identified by webhook name. (GET /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Automation/automationAccounts/{automationAccountName}/webhooks/{webhookName})
- update_webhook_identified_webhook: Update the webhook identified by webhook name. (PATCH /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Automation/automationAccounts/{automationAccountName}/webhooks/{webhookName})
- delete_webhook_name: Delete the webhook by name. (DELETE /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Automation/automationAccounts/{automationAccountName}/webhooks/{webhookName})
- create_generates_uri_use_creating: Generates a Uri for use in creating a webhook. (POST /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Automation/automationAccounts/{automationAccountName}/webhooks/generateUri)

## Fields

### Webhooks (Create webhook subscription)
- `delivery_url`: string [REQUIRED] (format: uri) — The delivery url of the webhook endpoint.
- `description`: string [OPTIONAL] — A description of the object.
- `events`: array [REQUIRED] — The list of subscribed events for this webhook. [`*`] indicates that all events are enabled.
- `status`: string [REQUIRED] (enum: enabled, disabled) — The status of the webhook.
- `unified_api`: string [REQUIRED] (enum: accounting, ats, calendar, crm, csp, ...) — Name of Apideck Unified API

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

**Required fields reference:**
```json
{
  "delivery_url": "example_delivery_url",
  "status": "example_status",
  "unified_api": "example_unified_api"
}
```

## Response

**Subscription object:**
- `id`: string — Unique subscription identifier
- `name`: string — Subscription name or title
- `status`: string — Current status
- `type`: string — Subscription type or category
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
