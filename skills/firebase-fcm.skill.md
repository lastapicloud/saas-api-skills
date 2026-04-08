---
name: firebase-fcm
description: Send push notifications via Firebase Cloud Messaging. Use when the user
  mentions firebase fcm, fcm, push notification, cloud messaging, mobile notification.
version: 1.0.0
skill_type: external
base_url_env: FIREBASE_FCM_BASE_URL
auth_env_var: FIREBASE_FCM_SERVER_KEY
auth_type: bearer
triggers:
  - firebase fcm
  - fcm
  - push notification
  - cloud messaging
  - mobile notification
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires FIREBASE_FCM_BASE_URL and FIREBASE_FCM_SERVER_KEY environment
  variables.
---

# Firebase-Fcm

Send push notifications via Firebase Cloud Messaging. Use when the user mentions firebase fcm, fcm, push notification, cloud messaging, mobile notification.

## API Endpoints

- **POST** `/v1/projects/{project_id}/messages:send` - Send message
- **GET** `/v1/projects/{project_id}/topics` - List topics
- **POST** `/iid/v1/{token}/rel/topics/{topic}` - Subscribe to topic
- **DELETE** `/iid/v1/{token}/rel/topics/{topic}` - Unsubscribe from topic
- **POST** `/v1/projects/{project_id}/messages:send` - Send to topic
- **GET** `/iid/info/{token}` - Get token info
- **GET** `/v1beta/{name}` - Gets a single linked storage bucket.
- **GET** `/v1beta/{parent}/buckets` - Lists the linked storage buckets for a project.
- **POST** `/v1beta/{bucket}:addFirebase` - Links a Google Cloud Storage bucket to a Firebase project.
- **POST** `/v1beta/{bucket}:removeFirebase` - Unlinks a linked Google Cloud Storage bucket from a Firebase project.
- **POST** `/v1/installAttribution` - Get iOS strong/weak-match info for post-install attribution.
- **POST** `/v1/managedShortLinks:create` - Creates a managed short Dynamic Link given either a valid long Dynamic Link or details such as Dynamic Link domain,
- **POST** `/v1/reopenAttribution` - Get iOS reopen attribution for app universal link open deeplinking.
- **POST** `/v1/shortLinks` - Creates a short Dynamic Link given either a valid long Dynamic Link or details such as Dynamic Link domain, Android and
- **GET** `/v1/{dynamicLink}/linkStats` - Fetches analytics stats of a short Dynamic Link for a given duration. Metrics include number of clicks, redirects,

## Actions

- create: Send message (POST /v1/projects/{project_id}/messages:send)
- list: List topics (GET /v1/projects/{project_id}/topics)
- add_topics: Subscribe to topic (POST /iid/v1/{token}/rel/topics/{topic})
- delete: Unsubscribe from topic (DELETE /iid/v1/{token}/rel/topics/{topic})
- create_messagessend: Send to topic (POST /v1/projects/{project_id}/messages:send)
- get_by_id: Get token info (GET /iid/info/{token})
- get_by_id_v1beta: Gets a single linked storage bucket. (GET /v1beta/{name})
- list_buckets: Lists the linked storage buckets for a project. (GET /v1beta/{parent}/buckets)
- create_v1beta: Links a Google Cloud Storage bucket to a Firebase project. (POST /v1beta/{bucket}:addFirebase)
- create_v1beta_2: Unlinks a linked Google Cloud Storage bucket from a Firebase project. (POST /v1beta/{bucket}:removeFirebase)
- create_installattribution: Get iOS strong/weak-match info for post-install attribution. (POST /v1/installAttribution)
- create_managedshortlinkscreate: Creates a managed short Dynamic Link given either a valid long Dynamic Link or d (POST /v1/managedShortLinks:create)
- create_reopenattribution: Get iOS reopen attribution for app universal link open deeplinking. (POST /v1/reopenAttribution)
- create_shortlinks: Creates a short Dynamic Link given either a valid long Dynamic Link or details s (POST /v1/shortLinks)
- list_linkstats: Fetches analytics stats of a short Dynamic Link for a given duration. Metrics in (GET /v1/{dynamicLink}/linkStats)

## Fields

- `message`: object [REQUIRED for send]
- `token`: string [REQUIRED for send to device]
- `topic`: string [OPTIONAL]
- `notification`: object [OPTIONAL] (title, body)

## Example Request Bodies

**Send Message to Device:**
```json
{"message": {"token": "device_token_abc123", "notification": {"title": "New Update", "body": "Version 2.0 is now available"}}}
```

**Send Message to Topic:**
```json
{"message": {"topic": "news", "notification": {"title": "Breaking News", "body": "Important announcement"}}}
