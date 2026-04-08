---
name: suprsend-notifications
description: Send multi-channel notifications via SuprSend. Use when the user mentions
  suprsend, notification, notify, workflow, channel.
version: 1.0.0
skill_type: external
base_url_env: SUPRSEND_BASE_URL
auth_env_var: SUPRSEND_API_KEY
auth_user_env: SUPRSEND_API_SECRET
auth_type: header
triggers:
  - suprsend
  - notification
  - notify
  - workflow
  - channel
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires SUPRSEND_BASE_URL and SUPRSEND_API_KEY environment variables.
---

# Suprsend-Notifications

Send multi-channel notifications via SuprSend. Use when the user mentions suprsend, notification, notify, workflow, channel.

## API Endpoints

- **POST** `/v1/trigger` - Trigger workflow
- **POST** `/v1/{distinct_id}/event` - Track event
- **POST** `/v1/subscriber/{distinct_id}` - Create subscriber profile
- **GET** `/v1/subscriber/{distinct_id}` - Get subscriber
- **PATCH** `/v1/subscriber/{distinct_id}` - Update subscriber
- **GET** `/v1/brand` - List brands
- **GET** `/v1/template` - List templates

## Actions

- create: Trigger workflow (POST /v1/trigger)
- create_event: Track event (POST /v1/{distinct_id}/event)
- add_subscriber: Create subscriber profile (POST /v1/subscriber/{distinct_id})
- get_by_id: Get subscriber (GET /v1/subscriber/{distinct_id})
- update: Update subscriber (PATCH /v1/subscriber/{distinct_id})
- list: List brands (GET /v1/brand)
- list_template: List templates (GET /v1/template)

## Fields

- `workflow`: string [REQUIRED for trigger]
- `recipients`: array [REQUIRED for trigger]
- `data`: object [OPTIONAL]

## Example Request Bodies

**Trigger Workflow:**
```json
{"workflow": "order-confirmation", "recipients": [{"distinct_id": "user_123"}], "data": {"order_id": "ORD-456", "amount": 99.99}}
```

**Update Subscriber:**
```json
{"name": "Jane Doe", "email": "jane@example.com"}
