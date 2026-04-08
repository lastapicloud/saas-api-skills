---
name: box-storage
description: Manage Box files, folders, and collaborations. Use when the user mentions
  box, file, folder, upload, storage, collaboration.
version: 1.0.0
skill_type: external
base_url_env: BOX_BASE_URL
auth_env_var: BOX_ACCESS_TOKEN
auth_type: bearer
triggers:
  - box
  - file
  - folder
  - upload
  - storage
  - collaboration
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires BOX_BASE_URL and BOX_ACCESS_TOKEN environment variables.
---

# Box-Storage

Manage Box files, folders, and collaborations. Use when the user mentions box, file, folder, upload, storage, collaboration.

## API Endpoints

- **GET** `/2.0/folders/{folderId}/items` - List items in a folder
- **GET** `/2.0/files/{fileId}` - Get file info
- **DELETE** `/2.0/files/{fileId}` - Delete a file
- **POST** `/2.0/folders` - Create a folder
- **GET** `/2.0/folders/{folderId}` - Get folder info
- **DELETE** `/2.0/folders/{folderId}` - Delete a folder
- **POST** `/2.0/files/{fileId}/copy` - Copy a file
- **GET** `/2.0/search` - Search for content
- **POST** `/2.0/collaborations` - Create a collaboration
- **GET** `/2.0/users/me` - Get current user
- **GET** `/collaborations` - List pending collaborations
- **POST** `/collaborations` - Create collaboration
- **PUT** `/collaborations/{collaboration_id}` - Update collaboration
- **DELETE** `/collaborations/{collaboration_id}` - Remove collaboration
- **GET** `/legal_hold_policies` - List all legal hold policies

## Actions

- list: List items in a folder (GET /2.0/folders/{folderId}/items)
- get_by_id: Get file info (GET /2.0/files/{fileId})
- delete: Delete a file (DELETE /2.0/files/{fileId})
- create: Create a folder (POST /2.0/folders)
- get_by_id_folders: Get folder info (GET /2.0/folders/{folderId})
- delete_folders: Delete a folder (DELETE /2.0/folders/{folderId})
- create_copy: Copy a file (POST /2.0/files/{fileId}/copy)
- search: Search for content (GET /2.0/search)
- create_collaborations: Create a collaboration (POST /2.0/collaborations)
- list_me: Get current user (GET /2.0/users/me)
- list_collaborations: List pending collaborations (GET /collaborations)
- create_collaborations_2: Create collaboration (POST /collaborations)
- update: Update collaboration (PUT /collaborations/{collaboration_id})
- delete_collaborations: Remove collaboration (DELETE /collaborations/{collaboration_id})
- list_legal_hold_policies: List all legal hold policies (GET /legal_hold_policies)

## Fields

- `name`: string [REQUIRED for create folder]
- `parent`: object [REQUIRED] with `id` (parent folder ID, "0" for root)
- `query`: string [REQUIRED for search]
- `accessible_by`: object [REQUIRED for collaboration] with `type`, `login`
- `role`: string [REQUIRED for collaboration] ("editor", "viewer", etc.)

## Example Request Bodies

**Create Folder:**
```json
{"name": "Q2 Reports", "parent": {"id": "0"}}
```

**Create Collaboration:**
```json
{"accessible_by": {"type": "user", "login": "colleague@example.com"}, "item": {"type": "folder", "id": "98765"}, "role": "editor"}
```
