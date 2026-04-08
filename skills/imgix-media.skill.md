---
name: imgix-media
description: Manage image sources and rendering via imgix. Use when the user mentions
  imgix, image, rendering, cdn, transform, media.
version: 1.0.0
skill_type: external
base_url_env: IMGIX_BASE_URL
auth_env_var: IMGIX_API_KEY
auth_type: bearer
triggers:
  - imgix
  - image
  - rendering
  - cdn
  - transform
  - media
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires IMGIX_BASE_URL and IMGIX_API_KEY environment variables.
---

# Imgix-Media

Manage image sources and rendering via imgix. Use when the user mentions imgix, image, rendering, cdn, transform, media.

## API Endpoints

- **GET** `/api/v1/sources` - List sources
- **POST** `/api/v1/sources` - Create source
- **GET** `/api/v1/sources/{sourceId}` - Get source
- **PATCH** `/api/v1/sources/{sourceId}` - Update source
- **DELETE** `/api/v1/sources/{sourceId}` - Delete source
- **POST** `/api/v1/sources/{sourceId}/assets` - Add asset
- **GET** `/api/v1/sources/{sourceId}/assets` - List assets

## Actions

- list: List sources (GET /api/v1/sources)
- create: Create source (POST /api/v1/sources)
- get_by_id: Get source (GET /api/v1/sources/{sourceId})
- update: Update source (PATCH /api/v1/sources/{sourceId})
- delete: Delete source (DELETE /api/v1/sources/{sourceId})
- create_assets: Add asset (POST /api/v1/sources/{sourceId}/assets)
- list_assets: List assets (GET /api/v1/sources/{sourceId}/assets)

## Fields

- `name`: string [REQUIRED for create]
- `type`: string [REQUIRED for create]
- `deployment`: object [REQUIRED for create]

## Example Request Bodies

**Create Source:**
```json
{"name": "product-images", "type": "webfolder", "deployment": {"type": "webfolder", "webfolder_base_url": "https://assets.example.com/images/"}}
```

**Add Asset:**
```json
{"origin_path": "/products/shoe-red.jpg"}
```
