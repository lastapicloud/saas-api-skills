---
name: dropbox-storage
description: Manage files and folders via Dropbox. Use when the user mentions dropbox,
  file, folder, storage, upload, download, share.
version: 1.0.0
skill_type: external
base_url_env: DROPBOX_BASE_URL
auth_env_var: DROPBOX_ACCESS_TOKEN
auth_type: bearer
triggers:
  - dropbox
  - file
  - folder
  - storage
  - upload
  - download
  - share
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires DROPBOX_BASE_URL and DROPBOX_ACCESS_TOKEN environment variables.
---

# Dropbox-Storage

Manage files and folders via Dropbox. Use when the user mentions dropbox, file, folder, storage, upload, download, share.

## API Endpoints

- **POST** `/2/files/list_folder` - List files in folder
- **POST** `/2/files/get_metadata` - Get file metadata
- **POST** `/2/files/create_folder_v2` - Create a folder
- **POST** `/2/files/delete_v2` - Delete a file or folder
- **POST** `/2/files/move_v2` - Move a file or folder
- **POST** `/2/files/copy_v2` - Copy a file or folder
- **POST** `/2/files/search_v2` - Search files
- **POST** `/2/sharing/create_shared_link_with_settings` - Create shared link

## Actions

- create: List files in folder (POST /2/files/list_folder)
- create_get_metadata: Get file metadata (POST /2/files/get_metadata)
- create_create_folder_v2: Create a folder (POST /2/files/create_folder_v2)
- create_delete_v2: Delete a file or folder (POST /2/files/delete_v2)
- create_move_v2: Move a file or folder (POST /2/files/move_v2)
- create_copy_v2: Copy a file or folder (POST /2/files/copy_v2)
- search: Search files (POST /2/files/search_v2)
- create_create_shared_link_with_settings: Create shared link (POST /2/sharing/create_shared_link_with_settings)

## Fields

- `path`: string [REQUIRED] (file or folder path)
- `from_path`: string [REQUIRED for move/copy]
- `to_path`: string [REQUIRED for move/copy]
- `query`: string [REQUIRED for search]

## Example Request Bodies

**Create a Folder:**
```json
{
  "path": "/Projects/2026-Q1",
  "autorename": false
}
```

**Move a File:**
```json
{
  "from_path": "/Documents/draft.docx",
  "to_path": "/Archive/draft.docx"
}
```
