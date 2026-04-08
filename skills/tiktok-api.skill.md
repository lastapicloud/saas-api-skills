---
name: tiktok-api
description: Manage videos and user info via TikTok API. Use when the user mentions
  tiktok, video, social media, creator, content.
version: 1.0.0
skill_type: external
base_url_env: TIKTOK_BASE_URL
auth_env_var: TIKTOK_ACCESS_TOKEN
auth_type: bearer
triggers:
  - tiktok
  - video
  - social media
  - creator
  - content
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires TIKTOK_BASE_URL and TIKTOK_ACCESS_TOKEN environment variables.
---

# Tiktok-Api

Manage videos and user info via TikTok API. Use when the user mentions tiktok, video, social media, creator, content.

## API Endpoints

- **POST** `/v2/video/list/` - List user videos
- **POST** `/v2/video/query/` - Query video info
- **POST** `/v2/research/user/info/` - Get user info
- **POST** `/v2/post/publish/video/init/` - Init video publish
- **POST** `/v2/post/publish/status/fetch/` - Get publish status
- **POST** `/v2/research/video/query/` - Research video query
- **GET** `/v2/user/info/` - Get current user info

## Actions

- create: List user videos (POST /v2/video/list/)
- create_query: Query video info (POST /v2/video/query/)
- create_info: Get user info (POST /v2/research/user/info/)
- create_init: Init video publish (POST /v2/post/publish/video/init/)
- create_fetch: Get publish status (POST /v2/post/publish/status/fetch/)
- create_query_2: Research video query (POST /v2/research/video/query/)
- list: Get current user info (GET /v2/user/info/)

## Fields

- `fields`: array [REQUIRED]
- `max_count`: integer [OPTIONAL]

## Example Request Bodies

**List User Videos:**
```json
{"fields": ["id", "title", "create_time", "like_count"], "max_count": 20}
```

**Query Video Info:**
```json
{"fields": ["id", "title", "view_count", "share_count"]}
