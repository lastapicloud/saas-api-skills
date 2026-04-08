---
name: filestack-uploads
description: Upload and transform files via Filestack. Use when the user mentions
  filestack, upload, file, transform, image, cdn.
version: 1.0.0
skill_type: external
base_url_env: FILESTACK_BASE_URL
auth_env_var: FILESTACK_API_KEY
auth_type: header
triggers:
  - filestack
  - upload
  - file
  - transform
  - image
  - cdn
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires FILESTACK_BASE_URL and FILESTACK_API_KEY environment variables.
---

# Filestack-Uploads

Upload and transform files via Filestack. Use when the user mentions filestack, upload, file, transform, image, cdn.

## API Endpoints

- **POST** `/api/store/S3` - Upload file
- **GET** `/api/file/{handle}` - Get file metadata
- **DELETE** `/api/file/{handle}` - Delete file
- **POST** `/api/pick` - Pick file
- **GET** `/{api_key}/{transforms}/{handle}` - Transform file
- **POST** `/api/store/S3?url={url}` - Store from URL

## Actions

- create: Upload file (POST /api/store/S3)
- get_by_id: Get file metadata (GET /api/file/{handle})
- delete: Delete file (DELETE /api/file/{handle})
- create_pick: Pick file (POST /api/pick)
- get_by_id_resource: Transform file (GET /{api_key}/{transforms}/{handle})
- create_s3urlurl: Store from URL (POST /api/store/S3?url={url})

## Fields

- `handle`: string [REQUIRED for get/delete]
- `url`: string [OPTIONAL]
- `transforms`: string [OPTIONAL]

## Example Request Bodies

**Store from URL:**
```json
{
  "url": "https://example.com/images/photo.jpg"
}
```

**Pick File:**
```json
{
  "sources": ["local_file_system", "url"],
  "accept": ["image/*", "application/pdf"]
}
```
