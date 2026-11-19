---
name: crisp-support
description: 'Manage Crisp conversations and contacts. Use when the user mentions
  crisp, conversation, message, chat, support.

  '
version: 1.0.0
skill_type: external
base_url_env: CRISP_BASE_URL
auth_env_var: CRISP_TOKEN_SECRET
auth_user_env: CRISP_TOKEN_ID
auth_type: basic
triggers:
  - crisp
  - conversation
  - message
  - chat
  - support
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires CRISP_BASE_URL and CRISP_TOKEN_SECRET environment variables.
annotations:
  readOnlyHint: false
  destructiveHint: false
  idempotentHint: false
---

# Crisp-Support

Manage Crisp conversations and contacts. Use when the user mentions crisp, conversation, message, chat, support.


## API Endpoints

- **GET** `/v1/plans/subscription` - List All Active Plan Subscriptions
- **PATCH** `/v1/plans/subscription/{website_id}/coupon` - Redeem Coupon For Website Plan Subscription
- **DELETE** `/v1/plans/subscription/{website_id}` - Unsubscribe Plan From Website
- **POST** `/v1/plans/subscription/{website_id}` - Subscribe Website To Plan
- **GET** `/v1/plugins/subscription` - List All Active Subscriptions
- **DELETE** `/v1/plugins/subscription/{website_id}/{plugin_id}` - Unsubscribe Plugin From Website
- **POST** `/v1/plugins/subscription/{website_id}` - Subscribe Website To Plugin
- **PUT** `/v1/plugins/subscription/{website_id}/{plugin_id}/settings` - Save Subscription Settings
- **PATCH** `/v1/plugins/subscription/{website_id}/{plugin_id}/settings` - Update Subscription Settings
- **POST** `/v1/website` - Create Website
- **GET** `/v1/website/{website_id}` - Get A Website
- **DELETE** `/v1/website/{website_id}` - Delete A Website
- **PATCH** `/v1/website/{website_id}/operators/email` - Send Email To Website Operators
- **PUT** `/v1/website/{website_id}/campaign/{campaign_id}` - Save A Campaign
- **GET** `/v1/plugin/connect/account` - ⭐ Get Connect Account

## Actions

- list: List All Active Plan Subscriptions (GET /v1/plans/subscription)
- patch_coupon: Redeem Coupon For Website Plan Subscription (PATCH /v1/plans/subscription/{website_id}/coupon)
- delete: Unsubscribe Plan From Website (DELETE /v1/plans/subscription/{website_id})
- add_subscription: Subscribe Website To Plan (POST /v1/plans/subscription/{website_id})
- list_active_subscriptions: List All Active Subscriptions (GET /v1/plugins/subscription)
- delete_unsubscribe_plugin_website: Unsubscribe Plugin From Website (DELETE /v1/plugins/subscription/{website_id}/{plugin_id})
- create_subscribe_website_plugin: Subscribe Website To Plugin (POST /v1/plugins/subscription/{website_id})
- put_settings: Save Subscription Settings (PUT /v1/plugins/subscription/{website_id}/{plugin_id}/settings)
- patch_settings: Update Subscription Settings (PATCH /v1/plugins/subscription/{website_id}/{plugin_id}/settings)
- create: Create Website (POST /v1/website)
- get_by_id: Get A Website (GET /v1/website/{website_id})
- delete_website: Delete A Website (DELETE /v1/website/{website_id})
- patch_email: Send Email To Website Operators (PATCH /v1/website/{website_id}/operators/email)
- update: Save A Campaign (PUT /v1/website/{website_id}/campaign/{campaign_id})
- get_connect_account: ⭐ Get Connect Account (GET /v1/plugin/connect/account)

## Fields

- `type`: string [REQUIRED for send message] ("text") — Resource type
- `content`: string [REQUIRED for send message] — Content body
- `from`: string [REQUIRED for send message] ("operator" or "user") — From
- `origin`: string [REQUIRED for send message] ("chat") — Origin

## Example Request Bodies

**Send Message:**
```json
{"type": "text", "content": "Hello! How can I help you today?", "from": "operator", "origin": "chat"}
```

**Update Conversation Metadata:**
```json
{"nickname": "VIP Customer", "email": "vip@example.com", "segments": ["enterprise"]}
```

## Response

**Subscription object:**
- `id`: string — Unique subscription identifier
- `name`: string — Subscription name or title
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
