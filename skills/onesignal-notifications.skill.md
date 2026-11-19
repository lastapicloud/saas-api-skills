---
name: onesignal-notifications
description: "Send push notifications, manage users, and segments in OneSignal. Use\
  \ when the user mentions onesignal, push notification, notification, segment, device,\
  \ player.\n (API 1.2.2)"
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
annotations:
  readOnlyHint: false
  destructiveHint: true
  idempotentHint: false
---

# Onesignal-Notifications

Send push notifications, manage users, and segments in OneSignal. Use when the user mentions onesignal, push notification, notification, segment, device, player.
 (API 1.2.2)

## API Endpoints

- **GET** `/players` - View devices
- **POST** `/players` - Add a device
- **PUT** `/players/{player_id}` - Edit device
- **DELETE** `/players/{player_id}` - Delete a user record
- **GET** `/notifications` - View notifications
- **POST** `/notifications` - Create notification
- **DELETE** `/notifications/{notification_id}` - Stop a scheduled or currently outgoing notification
- **GET** `/apps` - View apps
- **POST** `/apps` - Create an app
- **PUT** `/apps/{app_id}` - Update an app
- **PATCH** `/apps/{app_id}/subscriptions/{subscription_id}` - Updates an existing Subscription’s properties.
- **DELETE** `/apps/{app_id}/segments/{segment_id}` - Delete Segments

## Actions

- list: View devices (GET /players)
- create: Add a device (POST /players)
- update: Edit device (PUT /players/{player_id})
- delete: Delete a user record (DELETE /players/{player_id})
- get_view_notifications: View notifications (GET /notifications)
- create_notification: Create notification (POST /notifications)
- stop_scheduled_currently_outgoing: Stop a scheduled or currently outgoing notification (DELETE /notifications/{notification_id})
- get_view_apps: View apps (GET /apps)
- create_app: Create an app (POST /apps)
- update_app: Update an app (PUT /apps/{app_id})
- update_existing_subscriptions_properties: Updates an existing Subscription’s properties. (PATCH /apps/{app_id}/subscriptions/{subscription_id})
- delete_segments: Delete Segments (DELETE /apps/{app_id}/segments/{segment_id})

## Fields

### Players (Add a device)
- `id`: string [OPTIONAL] — The device's OneSignal ID
- `invalid_identifier`: boolean [OPTIONAL] — If true, this is the equivalent of a user being Unsubscribed
- `app_id`: string [OPTIONAL] — App unique identifier
- `device_type`: integer [REQUIRED] — Required
The device's platform:
  0 = iOS
  1 = Android
  2 = Amazon
  3 = WindowsPhone (MPNS)
  4 = Chrome Apps / Exten
- `external_user_id`: string [OPTIONAL] — a custom user ID
- `external_user_id_auth_hash`: string [OPTIONAL] — Only required if you have enabled Identity Verification and device_type is NOT 11 email.
- `email_auth_hash`: string [OPTIONAL] — Email - Only required if you have enabled Identity Verification and device_type is email (11).
- `identifier`: string [OPTIONAL] — Recommended: For Push Notifications, this is the Push Token Identifier from Google or Apple. For Apple Push identifiers,
- `language`: string [OPTIONAL] — Language code. Typically lower case two letters, except for Chinese where it must be one of zh-Hans or zh-Hant. Example:
- `timezone`: integer [OPTIONAL] — Number of seconds away from UTC. Example: -28800

- `game_version`: string [OPTIONAL] — Version of your app. Example: 1.1

- `device_model`: string [OPTIONAL] — Device make and model. Example: iPhone5,1

- `device_os`: string [OPTIONAL] — Device operating system version. Example: 7.0.4

- `ad_id`: string [OPTIONAL] — The ad id for the device's platform:
Android = Advertising Id
iOS = identifierForVendor
WP8.0 = DeviceUniqueId
WP8.1 = A
- `sdk`: string [OPTIONAL] — Name and version of the sdk/plugin that's calling this API method (if any)

### Apps (Create an app)
- `id`: string [OPTIONAL] — Unique identifier
- `name`: string [OPTIONAL] — The name of your app, as displayed on your apps list on the dashboard.  This can be renamed.
- `players`: integer [OPTIONAL] — Players value
- `messageable_players`: integer [OPTIONAL] — Messageable Players value
- `updated_at`: string [OPTIONAL] (format: date-time) — Last update timestamp
- `created_at`: string [OPTIONAL] (format: date-time) — Creation timestamp
- `android_gcm_sender_id`: string [OPTIONAL] — Android: Your Google Project number.  Also known as Sender ID.
- `gcm_key`: string [OPTIONAL] — Android: Your Google Push Messaging Auth Key
- `chrome_web_origin`: string [OPTIONAL] — Chrome (All Browsers except Safari) (Recommended): The URL to your website.  This field is required if you wish to enabl
- `chrome_key`: string [OPTIONAL] — Not for web push.  Your Google Push Messaging Auth Key if you use Chrome Apps / Extensions.
- `chrome_web_default_notification_icon`: string [OPTIONAL] — Chrome (All Browsers except Safari): Your default notification icon. Should be 256x256 pixels, min 80x80.
- `chrome_web_sub_domain`: string [OPTIONAL] — Chrome (All Browsers except Safari): A subdomain of your choice in order to support Web Push on non-HTTPS websites. This
- `apns_env`: string [OPTIONAL] (enum: sandbox, production) — iOS: Either sandbox or production
- `apns_p12`: string [OPTIONAL] — iOS: Your apple push notification p12 certificate file, converted to a string and Base64 encoded.
- `apns_p12_password`: string [OPTIONAL] — iOS: Required if using p12 certificate.  Password for the apns_p12 file.

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

## Response

**get_players response:**
- `total_count`: integer — Total Count value
- `offset`: integer — Pagination offset
- `limit`: integer — Maximum number of results
- `players`: array — List of players

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
