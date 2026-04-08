---
name: brightcove-video
description: Manage videos and players via Brightcove. Use when the user mentions
  brightcove, video, player, stream, media.
version: 1.0.0
skill_type: external
base_url_env: BRIGHTCOVE_BASE_URL
auth_env_var: BRIGHTCOVE_ACCESS_TOKEN
auth_type: bearer
triggers:
  - brightcove
  - video
  - player
  - stream
  - media
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires BRIGHTCOVE_BASE_URL and BRIGHTCOVE_ACCESS_TOKEN environment
  variables.
---

# Brightcove-Video

Manage videos and players via Brightcove. Use when the user mentions brightcove, video, player, stream, media.

## API Endpoints

- **GET** `/v1/accounts/{account_id}/videos` - List videos
- **POST** `/v1/accounts/{account_id}/videos` - Create a video
- **GET** `/v1/accounts/{account_id}/videos/{video_id}` - Get video by ID
- **PATCH** `/v1/accounts/{account_id}/videos/{video_id}` - Update a video
- **DELETE** `/v1/accounts/{account_id}/videos/{video_id}` - Delete a video
- **GET** `/v1/accounts/{account_id}/playlists` - List playlists
- **POST** `/v1/accounts/{account_id}/playlists` - Create a playlist
- **GET** `/v1/accounts/{account_id}/video_count` - Get video count

## Actions

- list: List videos (GET /v1/accounts/{account_id}/videos)
- create: Create a video (POST /v1/accounts/{account_id}/videos)
- get_by_id: Get video by ID (GET /v1/accounts/{account_id}/videos/{video_id})
- update: Update a video (PATCH /v1/accounts/{account_id}/videos/{video_id})
- delete: Delete a video (DELETE /v1/accounts/{account_id}/videos/{video_id})
- list_playlists: List playlists (GET /v1/accounts/{account_id}/playlists)
- create_playlists: Create a playlist (POST /v1/accounts/{account_id}/playlists)
- list_video_count: Get video count (GET /v1/accounts/{account_id}/video_count)

## Fields

- `name`: string [REQUIRED for create]
- `description`: string [OPTIONAL]
- `account_id`: string [REQUIRED]

## Example Request Bodies

**Create Video:**
```json
{"name": "Product Launch", "description": "Q1 2025 product launch video"}
```

**Update Video:**
```json
{"name": "Updated Product Launch", "description": "Revised Q1 2025 launch video"}
