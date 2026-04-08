---
name: uploadcare-media
description: Upload and manage files via Uploadcare. Use when the user mentions uploadcare,
  upload, file, image, media, cdn.
version: 1.0.0
skill_type: external
base_url_env: UPLOADCARE_BASE_URL
auth_env_var: UPLOADCARE_SECRET_KEY
auth_user_env: UPLOADCARE_PUBLIC_KEY
auth_type: header
triggers:
  - uploadcare
  - upload
  - file
  - image
  - media
  - cdn
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires UPLOADCARE_BASE_URL and UPLOADCARE_SECRET_KEY environment
  variables.
---

# Uploadcare-Media

Upload and manage files via Uploadcare. Use when the user mentions uploadcare, upload, file, image, media, cdn.

## API Endpoints

- **GET** `/files/` - List files
- **GET** `/files/{uuid}/` - Get file
- **DELETE** `/files/{uuid}/` - Delete file
- **POST** `/files/{uuid}/storage/` - Store file
- **POST** `/files/` - Copy file
- **GET** `/groups/` - List groups
- **GET** `/groups/{uuid}/` - Get group
- **POST** `/convert/document/` - Convert document

## Actions

- list: List files (GET /files/)
- get_by_id: Get file (GET /files/{uuid}/)
- delete: Delete file (DELETE /files/{uuid}/)
- create: Store file (POST /files/{uuid}/storage/)
- create_files: Copy file (POST /files/)
- list_groups: List groups (GET /groups/)
- get_by_id_groups: Get group (GET /groups/{uuid}/)
- create_document: Convert document (POST /convert/document/)

## Fields

- `uuid`: string [REQUIRED for get/delete]
- `source`: string [REQUIRED for copy]

## Example Request Bodies

**Copy File:**
```json
{"source": "https://example.com/image.png"}
```

**Convert Document:**
```json
{"uuid": "a1b2c3d4-5678-90ab-cdef-1234567890ab", "target_format": "pdf"}
