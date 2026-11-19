---
name: dropbox-storage
description: 'Manage files and folders via Dropbox. Use when the user mentions dropbox,
  file, folder, storage, upload, download, share.

  '
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
annotations:
  readOnlyHint: false
  destructiveHint: false
  idempotentHint: false
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
- get_file_metadata: Get file metadata (POST /2/files/get_metadata)
- create_folder: Create a folder (POST /2/files/create_folder_v2)
- delete_file_folder: Delete a file or folder (POST /2/files/delete_v2)
- move_file_folder: Move a file or folder (POST /2/files/move_v2)
- copy_file_folder: Copy a file or folder (POST /2/files/copy_v2)
- search: Search files (POST /2/files/search_v2)
- create_shared_link: Create shared link (POST /2/sharing/create_shared_link_with_settings)

## Fields

- `path`: string [REQUIRED] (file or folder path) — Path
- `from_path`: string [REQUIRED for move/copy] — From Path
- `to_path`: string [REQUIRED for move/copy] — To Path
- `query`: string [REQUIRED for search] — Search or filter query

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

## Response

**List Folder object:**
- `id`: string — Unique list folder identifier
- `name`: string — List Folder name or title
- `status`: string — Current status
- `created_at`: string — Creation timestamp (ISO 8601)
- `updated_at`: string — Last update timestamp (ISO 8601)

## Error Responses

| Status | Meaning |
|--------|---------|
| 400 | Invalid request body — check required fields and types |
| 401 | Authentication failed — verify API key or token is valid and not expired |
| 403 | Forbidden — insufficient permissions or scope for this action |
| 409 | Conflict — resource already exists or concurrent modification |
| 429 | Rate limited — too many requests, retry after delay |
| 500 | Server error — retry or check service status page |
