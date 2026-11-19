---
name: youtube-data
description: "Manage YouTube videos, playlists, and channels. Use when the user mentions\
  \ youtube, video, playlist, channel, subscriber.\n (API v1)"
version: 1.0.0
skill_type: external
base_url_env: YOUTUBE_BASE_URL
auth_env_var: GOOGLE_API_TOKEN
auth_type: bearer
triggers:
  - youtube
  - video
  - playlist
  - channel
  - subscriber
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires YOUTUBE_BASE_URL and GOOGLE_API_TOKEN environment variables.
annotations:
  readOnlyHint: false
  destructiveHint: true
  idempotentHint: false
---

# Youtube-Data

Manage YouTube videos, playlists, and channels. Use when the user mentions youtube, video, playlist, channel, subscriber.
 (API v1)

## API Endpoints

- **GET** `/youtube/v3/search` - Retrieves a list of search resources
- **POST** `/youtube/v3/abuseReports` - Inserts a new resource into this collection.
- **PUT** `/youtube/v3/captions` - Updates an existing resource.
- **DELETE** `/youtube/v3/captions` - Deletes a resource.
- **GET** `/v1/jobs` - Lists jobs.
- **POST** `/v1/jobs` - Creates a job and returns it.
- **DELETE** `/v1/jobs/{jobId}` - Deletes a job.
- **GET** `/v1/reportTypes` - Lists report types.
- **GET** `/v1/media/{resourceName}` - Method for media download. Download is supported on the URI `/v1/media/{+name}?alt=media`.

## Actions

- youtube_search_list: Retrieves a list of search resources (GET /youtube/v3/search)
- youtube_abuse_reports_insert: Inserts a new resource into this collection. (POST /youtube/v3/abuseReports)
- youtube_captions_update: Updates an existing resource. (PUT /youtube/v3/captions)
- youtube_captions_delete: Deletes a resource. (DELETE /youtube/v3/captions)
- youtubereporting_jobs_list: Lists jobs. (GET /v1/jobs)
- youtubereporting_jobs_create: Creates a job and returns it. (POST /v1/jobs)
- youtubereporting_jobs_delete: Deletes a job. (DELETE /v1/jobs/{jobId})
- youtubereporting_report_types_list: Lists report types. (GET /v1/reportTypes)
- youtubereporting_media_download: Method for media download. Download is supported on the URI `/v1/media/{+name}?a (GET /v1/media/{resourceName})

## Fields

### Jobs (Creates a job and returns it.)
- `createTime`: string [OPTIONAL] (format: google-datetime) — The creation date/time of the job.
- `expireTime`: string [OPTIONAL] (format: google-datetime) — The date/time when this job will expire/expired. After a job expired, no new reports are generated.
- `id`: string [OPTIONAL] — The server-generated ID of the job (max. 40 characters).
- `name`: string [OPTIONAL] — The name of the job (max. 100 characters).
- `reportTypeId`: string [OPTIONAL] — The type of reports this job creates. Corresponds to the ID of a ReportType.
- `systemManaged`: boolean [OPTIONAL] — True if this a system-managed job that cannot be modified by the user; otherwise false.

## Example Request Bodies

**Create Playlist:**
```json
{"snippet": {"title": "Tutorial Series", "description": "Step-by-step coding tutorials"}, "status": {"privacyStatus": "public"}}
```

**Add to Playlist:**
```json
{"snippet": {"playlistId": "PLxxxxxx", "resourceId": {"kind": "youtube#video", "videoId": "dQw4w9WgXcQ"}}}
```

## Response

**Job object:**
- `id`: string — Unique job identifier
- `name`: string — Job name or title
- `status`: string — Current status
- `type`: string — Job type or category
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
