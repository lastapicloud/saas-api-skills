---
name: knock-notifications
description: Send notifications and manage workflows via Knock. Use when the user
  mentions knock, notification, workflow, channel, subscriber.
version: 1.0.0
skill_type: external
base_url_env: KNOCK_BASE_URL
auth_env_var: KNOCK_API_KEY
auth_type: bearer
triggers:
  - knock
  - notification
  - workflow
  - channel
  - subscriber
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires KNOCK_BASE_URL and KNOCK_API_KEY environment variables.
---

# Knock-Notifications

Send notifications and manage workflows via Knock. Use when the user mentions knock, notification, workflow, channel, subscriber.

## API Endpoints

- **POST** `/v1/workflows/{key}/trigger` - Trigger workflow
- **GET** `/v1/users/{id}` - Get user
- **PUT** `/v1/users/{id}` - Identify user
- **DELETE** `/v1/users/{id}` - Delete user
- **GET** `/v1/users/{id}/messages` - List user messages
- **GET** `/v1/users/{id}/feeds/{feed_id}` - Get user feed
- **PUT** `/v1/users/{id}/channel_data/{channel_id}` - Set channel data
- **POST** `/v1/workflows/{key}/cancel` - Cancel workflow

## Actions

- create: Trigger workflow (POST /v1/workflows/{key}/trigger)
- get_by_id: Get user (GET /v1/users/{id})
- update: Identify user (PUT /v1/users/{id})
- delete: Delete user (DELETE /v1/users/{id})
- list: List user messages (GET /v1/users/{id}/messages)
- get_by_id_feeds: Get user feed (GET /v1/users/{id}/feeds/{feed_id})
- update_channel_data: Set channel data (PUT /v1/users/{id}/channel_data/{channel_id})
- create_cancel: Cancel workflow (POST /v1/workflows/{key}/cancel)

## Fields

- `recipients`: array [REQUIRED for trigger]
- `data`: object [OPTIONAL]
- `actor`: string [OPTIONAL]

## Example Request Bodies

**Trigger Workflow:**
```json
{"recipients": ["user-123", "user-456"], "data": {"message": "Your order has shipped!", "order_id": "ORD-789"}, "actor": "system"}
```

**Identify User:**
```json
{"name": "Jane Doe", "email": "jane@example.com", "timezone": "America/New_York"}
```
