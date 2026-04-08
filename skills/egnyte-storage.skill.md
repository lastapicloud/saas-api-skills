---
name: egnyte-storage
description: Manage files and folders via Egnyte. Use when the user mentions egnyte,
  file, folder, storage, document.
version: 1.0.0
skill_type: external
base_url_env: EGNYTE_BASE_URL
auth_env_var: EGNYTE_ACCESS_TOKEN
auth_type: bearer
triggers:
  - egnyte
  - file
  - folder
  - storage
  - document
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires EGNYTE_BASE_URL and EGNYTE_ACCESS_TOKEN environment variables.
---

# Egnyte-Storage

Manage files and folders via Egnyte. Use when the user mentions egnyte, file, folder, storage, document.

## API Endpoints

- **GET** `/pubapi/v1/fs/{path}` - List folder contents
- **POST** `/pubapi/v1/fs/{path}` - Create folder
- **DELETE** `/pubapi/v1/fs/{path}` - Delete file/folder
- **POST** `/pubapi/v1/fs-content/{path}` - Upload file
- **GET** `/pubapi/v1/fs-content/{path}` - Download file
- **POST** `/pubapi/v1/links` - Create shared link
- **GET** `/pubapi/v1/search` - Search files

## Actions

- get_by_id: List folder contents (GET /pubapi/v1/fs/{path})
- add_fs: Create folder (POST /pubapi/v1/fs/{path})
- delete: Delete file/folder (DELETE /pubapi/v1/fs/{path})
- add_fs_content: Upload file (POST /pubapi/v1/fs-content/{path})
- get_by_id_fs_content: Download file (GET /pubapi/v1/fs-content/{path})
- create: Create shared link (POST /pubapi/v1/links)
- search: Search files (GET /pubapi/v1/search)

## Fields

- `path`: string [REQUIRED]
- `action`: string [REQUIRED for create_folder] (add_folder)
- `query`: string [REQUIRED for search]

## Example Request Bodies

**Create Folder:**
```json
{"action": "add_folder"}
```

**Create Shared Link:**
```json
{"path": "/Shared/Documents/report.pdf", "type": "file", "accessibility": "anyone"}
