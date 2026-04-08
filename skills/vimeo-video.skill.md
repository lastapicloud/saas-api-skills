---
name: vimeo-video
description: Manage Vimeo videos, folders, and uploads. Use when the user mentions
  vimeo, video, upload, folder, channel.
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
---

# Vimeo-Video

Manage Vimeo videos, folders, and uploads. Use when the user mentions vimeo, video, upload, folder, channel.

## API Endpoints

- **GET** `/me/videos` - List my videos
- **GET** `/videos/{videoId}` - Get a video
- **PATCH** `/videos/{videoId}` - Update a video
- **DELETE** `/videos/{videoId}` - Delete a video
- **POST** `/me/videos` - Upload a video
- **GET** `/me/folders` - List folders
- **POST** `/me/folders` - Create a folder
- **GET** `/me/albums` - List showcases
- **GET** `/me` - Get current user
- **GET** `/videos/{videoId}/comments` - List comments
- **POST** `/me/albums` - Create an album
- **PATCH** `/me/albums/{album_id}` - Edit an album
- **PUT** `/me/categories/{category}` - Subscribe a user to a single category
- **DELETE** `/me/albums/{album_id}` - Delete an album
- **GET** `/groups` - Get all groups

## Actions

- list: List my videos (GET /me/videos)
- get_by_id: Get a video (GET /videos/{videoId})
- update: Update a video (PATCH /videos/{videoId})
- delete: Delete a video (DELETE /videos/{videoId})
- create: Upload a video (POST /me/videos)
- list_folders: List folders (GET /me/folders)
- create_folders: Create a folder (POST /me/folders)
- list_albums: List showcases (GET /me/albums)
- list_me: Get current user (GET /me)
- list_comments: List comments (GET /videos/{videoId}/comments)
- create_albums: Create an album (POST /me/albums)
- update_albums: Edit an album (PATCH /me/albums/{album_id})
- update_categories: Subscribe a user to a single category (PUT /me/categories/{category})
- delete_albums: Delete an album (DELETE /me/albums/{album_id})
- list_groups: Get all groups (GET /groups)

## Fields

- `name`: string [REQUIRED for update/folder]
- `description`: string [OPTIONAL]
- `privacy`: object [OPTIONAL] with `view` ("anybody", "nobody", "password", "unlisted")
- `upload`: object [REQUIRED for upload] with `approach` ("tus"), `size`

## Example Request Bodies

**Update Video:**
```json
{"name": "Product Demo 2026", "description": "Walkthrough of new features", "privacy": {"view": "unlisted"}}
```

**Create Folder:**
```json
{"name": "Marketing Videos"}
```
