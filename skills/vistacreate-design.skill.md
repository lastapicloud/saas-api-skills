---
name: vistacreate-design
description: Design automation, stock assets, and generative AI via VistaCreate. Use when the user mentions vistacreate, vista, stock images, stock videos, design template, creative assets, AI design.
version: 1.0.0
skill_type: external
base_url_env: VISTACREATE_BASE_URL
auth_env_var: VISTACREATE_API_KEY
auth_type: bearer
triggers:
  - vistacreate
  - vista
  - stock images
  - stock videos
  - design template
  - creative assets
  - AI design
license: Proprietary
metadata:
  author: lastapi
  version: 1.0.0
  documentation: https://create.vista.com/suite-api/doc/
---

# VistaCreate-Design

Design automation, stock assets, and generative AI via VistaCreate. Use when the user mentions vistacreate, vista, stock images, stock videos, design template, creative assets, AI design.

## API Endpoints

- **GET** `/oauth/token` - Get OAuth token
- **GET** `/v1/assets` - List available assets
- **GET** `/v1/assets/{assetId}` - Get asset details
- **POST** `/v1/assets/search` - Search for assets
- **GET** `/v1/templates` - List design templates
- **GET** `/v1/templates/{templateId}` - Get template details
- **POST** `/v1/designs` - Create a new design
- **GET** `/v1/designs/{designId}` - Get design details
- **PUT** `/v1/designs/{designId}` - Update a design
- **DELETE** `/v1/designs/{designId}` - Delete a design
- **POST** `/v1/designs/{designId}/export` - Export design
- **GET** `/v1/collections` - List asset collections
- **GET** `/v1/users/me` - Get current user

## Actions

- get_token: Get OAuth token (GET /oauth/token)
- list_assets: List available assets (GET /v1/assets)
- get_asset: Get asset details (GET /v1/assets/{assetId})
- search_assets: Search for assets (POST /v1/assets/search)
- list_templates: List design templates (GET /v1/templates)
- get_template: Get template details (GET /v1/templates/{templateId})
- create_design: Create a new design (POST /v1/designs)
- get_design: Get design details (GET /v1/designs/{designId})
- update_design: Update a design (PUT /v1/designs/{designId})
- delete_design: Delete a design (DELETE /v1/designs/{designId})
- export_design: Export design (POST /v1/designs/{designId}/export)
- list_collections: List asset collections (GET /v1/collections)
- get_user: Get current user (GET /v1/users/me)

## Fields

- `template_id`: string [REQUIRED for create] - Template ID
- `name`: string [REQUIRED for create] - Design name
- `query`: string [REQUIRED for search] - Search query
- `asset_type`: string [OPTIONAL] - Asset type (image, video, vector)
- `export_format`: string [OPTIONAL] - Export format (png, jpg, pdf)
- `dimensions`: object [OPTIONAL] - Output dimensions

## Example Request Bodies

**Search Assets:**
```json
{"query": "business meeting", "asset_type": "image", "limit": 10}
```

**Create Design:**
```json
{"template_id": "TEMPLATE_ID", "name": "My Design"}
```

**Export Design:**
```json
{"format": "png", "dimensions": {"width": 1920, "height": 1080}}
```
