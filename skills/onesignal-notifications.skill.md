---
name: onesignal-notifications
description: Send push notifications, manage users, and segments in OneSignal. Use
  when the user mentions onesignal, push notification, notification, segment, device,
  player.
version: 1.0.0
skill_type: external
base_url_env: ONESIGNAL_BASE_URL
auth_env_var: ONESIGNAL_REST_API_KEY
auth_type: header
triggers:
  - onesignal
  - push notification
  - notification
  - segment
  - device
  - player
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires ONESIGNAL_BASE_URL and ONESIGNAL_REST_API_KEY environment
  variables.
---

# Onesignal-Notifications

Send push notifications, manage users, and segments in OneSignal. Use when the user mentions onesignal, push notification, notification, segment, device, player.

## API Endpoints

- **POST** `/notifications` - Send a notification
- **GET** `/notifications/{notification_id}` - Get a notification
- **GET** `/notifications` - List notifications
- **DELETE** `/notifications/{notification_id}` - Cancel a notification
- **GET** `/players` - List devices/players
- **POST** `/players` - Add a device
- **GET** `/apps/{app_id}` - Get an app
- **GET** `/apps` - List apps (requires User Auth Key)
- **PUT** `/players/{player_id}` - Edit device
- **DELETE** `/players/{player_id}` - Delete a user record
- **POST** `/apps` - Create an app
- **PUT** `/apps/{app_id}` - Update an app
- **PATCH** `/apps/{app_id}/subscriptions/{subscription_id}` - Updates an existing Subscription’s properties.
- **DELETE** `/apps/{app_id}/segments/{segment_id}` - Delete Segments

## Actions

- create: Send a notification (POST /notifications)
- get_by_id: Get a notification (GET /notifications/{notification_id})
- list: List notifications (GET /notifications)
- delete: Cancel a notification (DELETE /notifications/{notification_id})
- list_players: List devices/players (GET /players)
- create_players: Add a device (POST /players)
- get_by_id_apps: Get an app (GET /apps/{app_id})
- list_apps: List apps (requires User Auth Key) (GET /apps)
- update: Edit device (PUT /players/{player_id})
- delete_players: Delete a user record (DELETE /players/{player_id})
- create_apps: Create an app (POST /apps)
- update_apps: Update an app (PUT /apps/{app_id})
- update_subscriptions: Updates an existing Subscription’s properties. (PATCH /apps/{app_id}/subscriptions/{subscription_id})
- delete_segments: Delete Segments (DELETE /apps/{app_id}/segments/{segment_id})

## Fields

- `app_id`: string [REQUIRED for most actions] (OneSignal App ID)
- `notification_id`: string [REQUIRED for get/cancel notification] (notification ID)
- `contents`: object [REQUIRED for send_notification] (message content by language, e.g. {"en": "Hello"})
- `headings`: object [OPTIONAL for send_notification] (notification title by language)
- `included_segments`: array [OPTIONAL for send_notification] (target segments, e.g. ["All"])
- `include_player_ids`: array [OPTIONAL for send_notification] (specific device IDs)
- `url`: string [OPTIONAL for send_notification] (URL to open on click)
- `data`: object [OPTIONAL for send_notification] (custom data payload)
- `device_type`: integer [REQUIRED for add_device] (0=iOS, 1=Android, 5=Chrome, etc.)
- `identifier`: string [REQUIRED for add_device] (push token)
- `limit`: integer [OPTIONAL] (results per page)
- `offset`: integer [OPTIONAL] (pagination offset)

## Example Request Bodies

**Send Notification:**
```json
{"app_id": "your-app-id", "contents": {"en": "Hello from PythonREST!"}, "headings": {"en": "Test Notification"}, "included_segments": ["All"]}
```

**Send to Specific Devices:**
```json
{"app_id": "your-app-id", "contents": {"en": "Personal message"}, "include_player_ids": ["device-id-1", "device-id-2"]}
```

**Add Device:**
```json
{"app_id": "your-app-id", "device_type": 1, "identifier": "push-token-abc123"}
```
