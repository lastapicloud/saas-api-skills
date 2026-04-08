---
name: onedrive-storage
description: Manage files and folders via OneDrive. Use when the user mentions onedrive,
  file, folder, storage, microsoft, sharepoint.
version: 1.0.0
skill_type: external
base_url_env: ONEDRIVE_BASE_URL
auth_env_var: ONEDRIVE_ACCESS_TOKEN
auth_type: bearer
triggers:
  - onedrive
  - file
  - folder
  - storage
  - microsoft
  - sharepoint
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires ONEDRIVE_BASE_URL and ONEDRIVE_ACCESS_TOKEN environment variables.
---

# Onedrive-Storage

Manage files and folders via OneDrive. Use when the user mentions onedrive, file, folder, storage, microsoft, sharepoint.

## API Endpoints

- **GET** `/me/drive/root/children` - List root items
- **GET** `/me/drive/items/{item-id}/children` - List folder items
- **GET** `/me/drive/items/{item-id}` - Get item
- **DELETE** `/me/drive/items/{item-id}` - Delete item
- **PUT** `/me/drive/items/{item-id}/content` - Upload file
- **GET** `/me/drive/items/{item-id}/content` - Download file
- **POST** `/me/drive/items/{parent-id}/children` - Create folder
- **GET** `/me/drive/search(q='{query}')` - Search files

## Actions

- list: List root items (GET /me/drive/root/children)
- list_children: List folder items (GET /me/drive/items/{item-id}/children)
- get_by_id: Get item (GET /me/drive/items/{item-id})
- delete: Delete item (DELETE /me/drive/items/{item-id})
- put_content: Upload file (PUT /me/drive/items/{item-id}/content)
- list_content: Download file (GET /me/drive/items/{item-id}/content)
- create: Create folder (POST /me/drive/items/{parent-id}/children)
- search: Search files (GET /me/drive/search(q='{query}'))

## Fields

- `name`: string [REQUIRED for create folder]
- `folder`: object [REQUIRED for create folder]
- `query`: string [REQUIRED for search]

## Example Request Bodies

**Create a Folder:**
```json
{
  "name": "Project Documents",
  "folder": {}
}
```

**Upload File (metadata):**
```json
{
  "name": "report.pdf",
  "description": "Quarterly financial report"
}
```
