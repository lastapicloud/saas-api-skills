---
name: egnyte-storage
description: 'Manage files and folders via Egnyte. Use when the user mentions egnyte,
  file, folder, storage, document.

  '
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
annotations:
  readOnlyHint: false
  destructiveHint: true
  idempotentHint: false
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
- download_file: Download file (GET /pubapi/v1/fs-content/{path})
- create: Create shared link (POST /pubapi/v1/links)
- search: Search files (GET /pubapi/v1/search)

## Fields

- `path`: string [REQUIRED] — Path
- `action`: string [REQUIRED for create_folder] (add_folder) — Action
- `query`: string [REQUIRED for search] — Search or filter query

## Example Request Bodies

**Create Folder:**
```json
{"action": "add_folder"}
```

**Create Shared Link:**
```json
{"path": "/Shared/Documents/report.pdf", "type": "file", "accessibility": "anyone"}

## Response

**F object:**
- `id`: string — Unique f identifier
- `name`: string — F name or title
- `status`: string — Current status
- `created_at`: string — Creation timestamp (ISO 8601)
- `updated_at`: string — Last update timestamp (ISO 8601)

## Error Responses

| Status | Meaning |
|--------|---------|
| 400 | Invalid request body — check required fields and types |
| 401 | Authentication failed — verify API key or token is valid and not expired |
| 403 | Forbidden — insufficient permissions or scope for this action |
| 404 | Resource not found — check the ID or identifier |
| 409 | Conflict — resource already exists or concurrent modification |
| 429 | Rate limited — too many requests, retry after delay |
| 500 | Server error — retry or check service status page |
