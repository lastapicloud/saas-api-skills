---
name: frameio-video
description: Video review and collaboration via Frame.io. Use when the user mentions frame.io, video review, video collaboration, creative review, asset management.
version: 1.0.0
skill_type: external
base_url_env: FRAMEIO_BASE_URL
auth_env_var: FRAMEIO_TOKEN
auth_type: bearer
triggers:
  - frame.io
  - video review
  - video collaboration
  - creative review
  - asset management
license: Proprietary
metadata:
  author: lastapi
  version: 1.0.0
  documentation: https://developer.frame.io/
---

# Frameio-Video

Video review and collaboration via Frame.io. Use when the user mentions frame.io, video review, video collaboration, creative review, asset management.

## API Endpoints

- **GET** `/v2/assets` - List assets
- **POST** `/v2/assets` - Create asset
- **GET** `/v2/assets/{id}` - Get asset
- **PUT** `/v2/assets/{id}` - Update asset
- **DELETE** `/v2/assets/{id}` - Delete asset
- **GET** `/v2/projects` - List projects
- **POST** `/v2/projects` - Create project
- **GET** `/v2/projects/{id}` - Get project
- **GET** `/v2/review_links` - List review links
- **POST** `/v2/review_links` - Create review link
- **GET** `/v2/comments` - List comments
- **POST** `/v2/comments` - Create comment

## Actions

- list_assets: List assets (GET /v2/assets)
- create_asset: Create asset (POST /v2/assets)
- get_asset: Get asset (GET /v2/assets/{id})
- update_asset: Update asset (PUT /v2/assets/{id})
- delete_asset: Delete asset (DELETE /v2/assets/{id})
- list_projects: List projects (GET /v2/projects)
- create_project: Create project (POST /v2/projects)
- get_project: Get project (GET /v2/projects/{id})
- list_review_links: List review links (GET /v2/review_links)
- create_review_link: Create review link (POST /v2/review_links)
- list_comments: List comments (GET /v2/comments)
- create_comment: Create comment (POST /v2/comments)

## Fields

- `projectId`: string [REQUIRED for create] - Project ID
- `parentId`: string [OPTIONAL] - Parent folder ID
- `name`: string [REQUIRED for create] - Asset name
- `type`: string [REQUIRED] - Asset type (file, folder)
- `filesize`: integer [OPTIONAL] - File size
- `notes`: string [OPTIONAL] - Notes/comments

## Example Request Bodies

**Create Asset:**
```json
{"projectId": "PROJECT_ID", "name": "video.mp4", "type": "file", "filesize": 52428800}
```

**Create Review Link:**
```json
{"projectId": "PROJECT_ID", "name": "Client Review"}
```

**Create Comment:**
```json
{"assetId": "ASSET_ID", "text": "Great work!", "timestamp": 120.5}
```
