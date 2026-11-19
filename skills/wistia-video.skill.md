---
name: wistia-video
description: 'Manage videos and projects via Wistia. Use when the user mentions wistia,
  video, hosting, media, player.

  '
version: 1.0.0
skill_type: external
base_url_env: WISTIA_BASE_URL
auth_env_var: WISTIA_API_TOKEN
auth_type: bearer
triggers:
  - wistia
  - video
  - hosting
  - media
  - player
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires WISTIA_BASE_URL and WISTIA_API_TOKEN environment variables.
annotations:
  readOnlyHint: false
  destructiveHint: true
  idempotentHint: false
---

# Wistia-Video

Manage videos and projects via Wistia. Use when the user mentions wistia, video, hosting, media, player.


## API Endpoints

- **GET** `/v1/medias.json` - List videos
- **GET** `/v1/medias/{id}.json` - Get video
- **PATCH** `/v1/medias/{id}.json` - Update video
- **DELETE** `/v1/medias/{id}.json` - Delete video
- **GET** `/v1/projects.json` - List projects
- **POST** `/v1/projects.json` - Create project
- **GET** `/v1/projects/{id}.json` - Get project
- **GET** `/v1/medias/{id}/stats.json` - Get video stats

## Actions

- list: List videos (GET /v1/medias.json)
- get_video: Get video (GET /v1/medias/{id}.json)
- patch_medias: Update video (PATCH /v1/medias/{id}.json)
- delete_medias: Delete video (DELETE /v1/medias/{id}.json)
- list_projects: List projects (GET /v1/projects.json)
- create: Create project (POST /v1/projects.json)
- get_project: Get project (GET /v1/projects/{id}.json)
- get_video_stats: Get video stats (GET /v1/medias/{id}/stats.json)

## Fields

- `name`: string [OPTIONAL] — Display name
- `description`: string [OPTIONAL] — Human-readable description

## Example Request Bodies

**Create Project:**
```json
{"name": "Product Demos"}
```

**Update Video:**
```json
{"name": "Updated Product Demo", "description": "Revised walkthrough of key features"}
```

## Response

**Media object:**
- `id`: string — Unique media identifier
- `name`: string — Media name or title
- `status`: string — Current status
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
