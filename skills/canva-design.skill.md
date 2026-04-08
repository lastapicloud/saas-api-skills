---
name: canva-design
description: Manage designs and assets via Canva. Use when the user mentions canva,
  design, template, graphic, image, brand.
version: 1.0.0
skill_type: external
base_url_env: CANVA_BASE_URL
auth_env_var: CANVA_ACCESS_TOKEN
auth_type: bearer
triggers:
  - canva
  - design
  - template
  - graphic
  - image
  - brand
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires CANVA_BASE_URL and CANVA_ACCESS_TOKEN environment variables.
---

# Canva-Design

Manage designs and assets via Canva. Use when the user mentions canva, design, template, graphic, image, brand.

## API Endpoints

- **GET** `/v1/designs` - List designs
- **POST** `/v1/designs` - Create a design
- **GET** `/v1/designs/{designId}` - Get design by ID
- **GET** `/v1/designs/{designId}/export` - Export a design
- **GET** `/v1/brand-templates` - List brand templates
- **POST** `/v1/asset-uploads` - Upload an asset
- **GET** `/v1/users/me` - Get current user
- **GET** `/v1/folders` - List folders
- **POST** `/v1/folders/move` - Moves an item to another folder. You must specify the folder ID of the destination folder, as well as the ID of the
- **GET** `/v1/folders/{folderId}` - Gets the name and other details of a folder using a folder's `folderID`.
- **PATCH** `/v1/folders/{folderId}` - Updates a folder's details using its `folderID`.
Currently, you can only update a folder's name.
- **DELETE** `/v1/folders/{folderId}` - Deletes a folder with the specified `folderID`.
Deleting a folder moves the user's content in the folder to
- **GET** `/v1/assets/{assetId}` - You can retrieve the metadata of an asset by specifying its `assetId`.
- **PATCH** `/v1/assets/{assetId}` - You can update the name and tags of an asset by specifying its `assetId`. Updating the tags
replaces all existing tags
- **DELETE** `/v1/assets/{assetId}` - You can delete an asset by specifying its `assetId`. This operation mirrors the behavior
in the Canva UI. Deleting an

## Actions

- list: List designs (GET /v1/designs)
- create: Create a design (POST /v1/designs)
- get_by_id: Get design by ID (GET /v1/designs/{designId})
- list_export: Export a design (GET /v1/designs/{designId}/export)
- list_brand_templates: List brand templates (GET /v1/brand-templates)
- create_asset_uploads: Upload an asset (POST /v1/asset-uploads)
- list_me: Get current user (GET /v1/users/me)
- list_folders: List folders (GET /v1/folders)
- create_move: Moves an item to another folder. You must specify the folder ID of the destinati (POST /v1/folders/move)
- get_by_id_folders: Gets the name and other details of a folder using a folder's `folderID`. (GET /v1/folders/{folderId})
- update: Updates a folder's details using its `folderID`.
Currently, you can only update (PATCH /v1/folders/{folderId})
- delete: Deletes a folder with the specified `folderID`.
Deleting a folder moves the user (DELETE /v1/folders/{folderId})
- get_by_id_assets: You can retrieve the metadata of an asset by specifying its `assetId`. (GET /v1/assets/{assetId})
- update_assets: You can update the name and tags of an asset by specifying its `assetId`. Updati (PATCH /v1/assets/{assetId})
- delete_assets: You can delete an asset by specifying its `assetId`. This operation mirrors the (DELETE /v1/assets/{assetId})

## Fields

- `design_type`: string [REQUIRED for create]
- `title`: string [OPTIONAL]

## Example Request Bodies

**Create Design:**
```json
{"design_type": "Presentation", "title": "Q2 Sales Deck"}
```

**Upload Asset:**
```json
{"name": "company-logo.png", "folder_id": "folder_xyz789"}
```
