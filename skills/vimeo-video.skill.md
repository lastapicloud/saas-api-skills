---
name: vimeo-video
description: "Manage Vimeo videos, folders, and uploads. Use when the user mentions\
  \ vimeo, video, upload, folder, channel.\n (API 3.4)"
version: 1.0.0
skill_type: external
base_url_env: VIMEO_BASE_URL
auth_env_var: VIMEO_ACCESS_TOKEN
auth_type: bearer
triggers:
  - vimeo
  - video
  - upload
  - folder
  - channel
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires VIMEO_BASE_URL and VIMEO_ACCESS_TOKEN environment variables.
annotations:
  readOnlyHint: false
  destructiveHint: true
  idempotentHint: false
---

# Vimeo-Video

Manage Vimeo videos, folders, and uploads. Use when the user mentions vimeo, video, upload, folder, channel.
 (API 3.4)

## API Endpoints

- **GET** `/me` - Get a user
- **POST** `/me/albums` - Create an album
- **PATCH** `/me/albums/{album_id}` - Edit an album
- **PUT** `/me/categories/{category}` - Subscribe a user to a single category
- **DELETE** `/me/albums/{album_id}` - Delete an album
- **GET** `/groups` - Get all groups
- **POST** `/groups` - Create a group
- **DELETE** `/groups/{group_id}` - Delete a group
- **PUT** `/groups/{group_id}/videos/{video_id}` - Add a video to a group
- **GET** `/videos` - Search for videos
- **PATCH** `/videos/{video_id}` - Edit a video
- **PUT** `/videos/{video_id}/categories` - Suggest categories for a video
- **DELETE** `/videos/{video_id}` - Delete a video
- **POST** `/videos/{video_id}/comments` - Add a comment to a video
- **GET** `/channels` - Get all channels

## Actions

- list: Get a user (GET /me)
- create: Create an album (POST /me/albums)
- update: Edit an album (PATCH /me/albums/{album_id})
- update_subscribe_user_single_category: Subscribe a user to a single category (PUT /me/categories/{category})
- delete: Delete an album (DELETE /me/albums/{album_id})
- get_groups: Get all groups (GET /groups)
- create_group: Create a group (POST /groups)
- delete_group: Delete a group (DELETE /groups/{group_id})
- add_video_group: Add a video to a group (PUT /groups/{group_id}/videos/{video_id})
- search_videos: Search for videos (GET /videos)
- update_edit_video: Edit a video (PATCH /videos/{video_id})
- put_categories: Suggest categories for a video (PUT /videos/{video_id}/categories)
- delete_video: Delete a video (DELETE /videos/{video_id})
- add_comment_video: Add a comment to a video (POST /videos/{video_id}/comments)
- get_channels: Get all channels (GET /channels)

## Fields

- `name`: string [REQUIRED for update/folder] — Display name
- `description`: string [OPTIONAL] — Human-readable description
- `privacy`: object [OPTIONAL] with `view` ("anybody", "nobody", "password", "unlisted") — Privacy configuration
- `upload`: object [REQUIRED for upload] with `approach` ("tus"), `size` — Upload configuration

## Example Request Bodies

**Update Video:**
```json
{"name": "Product Demo 2026", "description": "Walkthrough of new features", "privacy": {"view": "unlisted"}}
```

**Create Folder:**
```json
{"name": "Marketing Videos"}
```

## Response

**Group object:**
- `id`: string — Unique group identifier
- `name`: string — Group name or title
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
