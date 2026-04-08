---
name: braze-engagement
description: Manage Braze campaigns, users, and messaging. Use when the user mentions
  braze, campaign, user, engagement, push notification, messaging.
version: 1.0.0
skill_type: external
base_url_env: BRAZE_BASE_URL
auth_env_var: BRAZE_API_KEY
auth_type: bearer
triggers:
  - braze
  - campaign
  - user
  - engagement
  - push notification
  - messaging
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires BRAZE_BASE_URL and BRAZE_API_KEY environment variables.
---

# Braze-Engagement

Manage Braze campaigns, users, and messaging. Use when the user mentions braze, campaign, user, engagement, push notification, messaging.

## API Endpoints

- **POST** `/users/track` - Track user attributes, events, and purchases
- **POST** `/users/identify` - Identify users
- **POST** `/users/delete` - Delete users
- **POST** `/users/export/ids` - Export user by ID
- **POST** `/messages/send` - Send a message
- **GET** `/campaigns/list` - List campaigns
- **GET** `/campaigns/details` - Get campaign details
- **POST** `/campaigns/trigger/send` - Trigger campaign send
- **GET** `/segments/list` - List segments
- **GET** `/canvas/list` - List canvases
- **GET** `/canvas/data_series` - Canvas Data Series Analytics
- **POST** `/canvas/trigger/schedule/create` - Schedule API Triggered Canvases
- **GET** `/kpi/dau/data_series` - Daily Active Users by Date
- **GET** `/kpi/mau/data_series` - Monthly Active Users for Last 30 Days
- **GET** `/kpi/new_users/data_series` - Daily New Users by Date

## Actions

- create: Track user attributes, events, and purchases (POST /users/track)
- create_identify: Identify users (POST /users/identify)
- create_delete: Delete users (POST /users/delete)
- create_ids: Export user by ID (POST /users/export/ids)
- create_send: Send a message (POST /messages/send)
- list: List campaigns (GET /campaigns/list)
- list_details: Get campaign details (GET /campaigns/details)
- create_send_2: Trigger campaign send (POST /campaigns/trigger/send)
- list_segments: List segments (GET /segments/list)
- list_canvas: List canvases (GET /canvas/list)
- list_data_series: Canvas Data Series Analytics (GET /canvas/data_series)
- create_schedule: Schedule API Triggered Canvases (POST /canvas/trigger/schedule/create)
- list_data_series_2: Daily Active Users by Date (GET /kpi/dau/data_series)
- list_data_series_3: Monthly Active Users for Last 30 Days (GET /kpi/mau/data_series)
- list_data_series_4: Daily New Users by Date (GET /kpi/new_users/data_series)

## Fields

- `attributes`: array [OPTIONAL for track] with user attribute objects
- `events`: array [OPTIONAL for track] with event objects
- `external_ids`: array [REQUIRED for export/delete]
- `campaign_id`: string [REQUIRED for trigger]
- `recipients`: array [REQUIRED for trigger] with `external_user_id`

## Example Request Bodies

**Track User Attributes:**
```json
{"attributes": [{"external_id": "user-001", "first_name": "Alex", "email": "alex@example.com", "plan": "premium"}]}
```

**Trigger Campaign Send:**
```json
{"campaign_id": "camp_abc123", "recipients": [{"external_user_id": "user-001"}, {"external_user_id": "user-002"}]}
```
