---
name: cloudflare-stream
description: Upload, manage, and stream videos via Cloudflare Stream. Use when the
  user mentions cloudflare stream, stream, video, live stream.
version: 1.0.0
skill_type: external
base_url_env: CLOUDFLARE_STREAM_BASE_URL
auth_env_var: CLOUDFLARE_API_TOKEN
auth_type: bearer
triggers:
  - cloudflare stream
  - stream
  - video
  - live stream
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires CLOUDFLARE_STREAM_BASE_URL and CLOUDFLARE_API_TOKEN environment
  variables.
---

# Cloudflare-Stream

Upload, manage, and stream videos via Cloudflare Stream. Use when the user mentions cloudflare stream, stream, video, live stream.

## API Endpoints

- **GET** `/v4/accounts/{account_id}/stream` - List videos
- **POST** `/v4/accounts/{account_id}/stream` - Upload a video
- **GET** `/v4/accounts/{account_id}/stream/{identifier}` - Get video by ID
- **DELETE** `/v4/accounts/{account_id}/stream/{identifier}` - Delete a video
- **POST** `/v4/accounts/{account_id}/stream/live_inputs` - Create a live input
- **GET** `/v4/accounts/{account_id}/stream/live_inputs` - List live inputs
- **GET** `/v4/accounts/{account_id}/stream/{identifier}/downloads` - Get download URL

## Actions

- list: List videos (GET /v4/accounts/{account_id}/stream)
- create: Upload a video (POST /v4/accounts/{account_id}/stream)
- get_by_id: Get video by ID (GET /v4/accounts/{account_id}/stream/{identifier})
- delete: Delete a video (DELETE /v4/accounts/{account_id}/stream/{identifier})
- create_live_inputs: Create a live input (POST /v4/accounts/{account_id}/stream/live_inputs)
- list_live_inputs: List live inputs (GET /v4/accounts/{account_id}/stream/live_inputs)
- list_downloads: Get download URL (GET /v4/accounts/{account_id}/stream/{identifier}/downloads)

## Fields

- `url`: string [OPTIONAL for upload] (URL to fetch video from)
- `meta`: object [OPTIONAL] (metadata key-value pairs)
- `account_id`: string [REQUIRED] (Cloudflare account ID)
- `identifier`: string [REQUIRED for get/delete] (video identifier)
- `requireSignedURLs`: boolean [OPTIONAL] (restrict playback to signed URLs)
- `allowedOrigins`: array [OPTIONAL] (list of allowed referrer origins)
- `mode`: string [REQUIRED for create live input] ("automatic" or "off")
- `timeoutSeconds`: integer [OPTIONAL for live input] (idle timeout)

## Example Request Bodies

**Upload a Video from URL:**
```json
{
  "url": "https://example.com/videos/demo.mp4",
  "meta": {
    "name": "Product Demo"
  },
  "requireSignedURLs": false
}
```

**Create a Live Input:**
```json
{
  "meta": {
    "name": "Weekly Standup Stream"
  },
  "recording": {
    "mode": "automatic",
    "timeoutSeconds": 300
  }
}
```
