---
name: imagekit-media
description: Upload and transform images via ImageKit. Use when the user mentions
  imagekit, image, upload, transform, media, cdn.
version: 1.0.0
skill_type: external
base_url_env: IMAGEKIT_BASE_URL
auth_env_var: IMAGEKIT_PRIVATE_KEY
auth_type: basic
triggers:
  - imagekit
  - image
  - upload
  - transform
  - media
  - cdn
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires IMAGEKIT_BASE_URL and IMAGEKIT_PRIVATE_KEY environment variables.
---

# Imagekit-Media

Upload and transform images via ImageKit. Use when the user mentions imagekit, image, upload, transform, media, cdn.

## API Endpoints

- **POST** `/v1/files/upload` - Upload file
- **GET** `/v1/files` - List files
- **GET** `/v1/files/{fileId}/details` - Get file details
- **DELETE** `/v1/files/{fileId}` - Delete file
- **PATCH** `/v1/files/{fileId}/details` - Update file details
- **POST** `/v1/files/move` - Move file
- **POST** `/v1/files/copy` - Copy file
- **GET** `/v1/files/purge/{requestId}` - Get purge status

## Actions

- create: Upload file (POST /v1/files/upload)
- list: List files (GET /v1/files)
- list_details: Get file details (GET /v1/files/{fileId}/details)
- delete: Delete file (DELETE /v1/files/{fileId})
- patch_details: Update file details (PATCH /v1/files/{fileId}/details)
- create_move: Move file (POST /v1/files/move)
- create_copy: Copy file (POST /v1/files/copy)
- get_by_id: Get purge status (GET /v1/files/purge/{requestId})

## Fields

- `file`: string [REQUIRED for upload] (base64 or URL)
- `fileName`: string [REQUIRED for upload]
- `folder`: string [OPTIONAL]

## Example Request Bodies

**Upload File:**
```json
{"file": "https://example.com/images/photo.jpg", "fileName": "photo.jpg", "folder": "/uploads/2024"}
```

**Move File:**
```json
{"sourceFilePath": "/uploads/2024/photo.jpg", "destinationPath": "/archive/2024/"}
```
