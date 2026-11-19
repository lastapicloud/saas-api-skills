---
name: cloudflare-stream
description: 'Upload, manage, and stream videos via Cloudflare Stream. Use when the
  user mentions cloudflare stream, stream, video, live stream.

  '
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
compatibility: 'Requires CLOUDFLARE_STREAM_BASE_URL and CLOUDFLARE_API_TOKEN environment
  variables.

  '
annotations:
  readOnlyHint: false
  destructiveHint: true
  idempotentHint: false
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
- create_live_input: Create a live input (POST /v4/accounts/{account_id}/stream/live_inputs)
- list_live_inputs: List live inputs (GET /v4/accounts/{account_id}/stream/live_inputs)
- get_download_url: Get download URL (GET /v4/accounts/{account_id}/stream/{identifier}/downloads)

## Fields

- `url`: string [OPTIONAL for upload] (URL to fetch video from) — URL
- `meta`: object [OPTIONAL] (metadata key-value pairs) — Meta configuration
- `account_id`: string [REQUIRED] (Cloudflare account ID) — Account unique identifier
- `identifier`: string [REQUIRED for get/delete] (video identifier) — Identifier
- `requireSignedURLs`: boolean [OPTIONAL] (restrict playback to signed URLs) — Whether requireSignedURLs is enabled
- `allowedOrigins`: array [OPTIONAL] (list of allowed referrer origins) — List of allowedOrigins
- `mode`: string [REQUIRED for create live input] ("automatic" or "off") — Mode
- `timeoutSeconds`: integer [OPTIONAL for live input] (idle timeout) — Timeoutseconds value

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

## Response

**Stream object:**
- `id`: string — Unique stream identifier
- `name`: string — Stream name or title
- `status`: string — Current status
- `created_at`: string — Creation timestamp (ISO 8601)
- `updated_at`: string — Last update timestamp (ISO 8601)


**Required fields reference:**
```json
{
  "account_id": "example_account_id",
  "identifier": "example_identifier"
}
```


**Required fields reference:**
```json
{
  "account_id": "example_account_id",
  "identifier": "example_identifier"
}
```

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
