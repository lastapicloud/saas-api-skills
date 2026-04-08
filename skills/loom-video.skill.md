---
name: loom-video
description: Video messaging via Loom. Use when the user mentions loom, video message, async video, screen recording, video update.
version: 1.0.0
skill_type: external
base_url_env: LOOM_BASE_URL
auth_env_var: LOOM_API_KEY
auth_type: bearer
triggers:
  - loom
  - video message
  - async video
  - screen recording
  - video update
license: Proprietary
metadata:
  author: lastapi
  version: 1.0.0
  documentation: https://www.loom.com/developer
---

# Loom-Video

Video messaging via Loom. Use when the user mentions loom, video message, async video, screen recording, video update.

## API Endpoints

- **GET** `/v1/videos` - List videos
- **POST** `/v1/videos` - Create video
- **GET** `/v1/videos/{id}` - Get video
- **PUT** `/v1/videos/{id}` - Update video
- **DELETE** `/v1/videos/{id}` - Delete video
- **GET** `/v1/videos/{id}/views` - Get video views
- **GET** `/v1/webhooks` - List webhooks
- **POST** `/v1/webhooks` - Create webhook
- **DELETE** `/v1/webhooks/{id}` - Delete webhook

## Actions

- list_videos: List videos (GET /v1/videos)
- create_video: Create video (POST /v1/videos)
- get_video: Get video (GET /v1/videos/{id})
- update_video: Update video (PUT /v1/videos/{id})
- delete_video: Delete video (DELETE /v1/videos/{id})
- get_views: Get video views (GET /v1/videos/{id}/views)
- list_webhooks: List webhooks (GET /v1/webhooks)
- create_webhook: Create webhook (POST /v1/webhooks)
- delete_webhook: Delete webhook (DELETE /v1/webhooks/{id})

## Fields

- `title`: string [REQUIRED for create] - Video title
- `url`: string [REQUIRED] - Video URL
- `duration`: integer [OPTIONAL] - Duration in seconds
- `thumbnailUrl`: string [OPTIONAL] - Thumbnail URL
- `callbackUrl`: string [OPTIONAL] - Webhook callback URL

## Example Request Bodies

**Create Video:**
```json
{"title": "Product Demo", "url": "https://loom.com/share/VIDEO_ID"}
```

**Update Video:**
```json
{"title": "Updated Demo", "callbackUrl": "https://example.com/webhook"}
```

**Create Webhook:**
```json
{"url": "https://example.com/webhook", "events": ["video.created", "video.deleted"]}
```
