---
name: wistia-video
description: Manage videos and projects via Wistia. Use when the user mentions wistia,
  video, hosting, media, player.
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
- list_medias: Get video (GET /v1/medias/{id}.json)
- patch_medias: Update video (PATCH /v1/medias/{id}.json)
- delete_medias: Delete video (DELETE /v1/medias/{id}.json)
- list_projects_json: List projects (GET /v1/projects.json)
- create: Create project (POST /v1/projects.json)
- list_projects: Get project (GET /v1/projects/{id}.json)
- list_stats_json: Get video stats (GET /v1/medias/{id}/stats.json)

## Fields

- `name`: string [OPTIONAL]
- `description`: string [OPTIONAL]

## Example Request Bodies

**Create Project:**
```json
{"name": "Product Demos"}
```

**Update Video:**
```json
{"name": "Updated Product Demo", "description": "Revised walkthrough of key features"}
```
