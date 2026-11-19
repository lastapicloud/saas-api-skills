---
name: minio-storage
description: 'Manage buckets and objects via MinIO S3-compatible storage. Use when
  the user mentions minio, s3, bucket, object, storage, upload.

  '
version: 1.0.0
skill_type: external
base_url_env: MINIO_BASE_URL
auth_env_var: MINIO_ACCESS_KEY
auth_user_env: MINIO_SECRET_KEY
auth_type: header
triggers:
  - minio
  - s3
  - bucket
  - object
  - storage
  - upload
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires MINIO_BASE_URL and MINIO_ACCESS_KEY environment variables.
annotations:
  readOnlyHint: false
  destructiveHint: true
  idempotentHint: false
---

# Minio-Storage

Manage buckets and objects via MinIO S3-compatible storage. Use when the user mentions minio, s3, bucket, object, storage, upload.


## API Endpoints

- **GET** `/` - List all buckets
- **PUT** `/{bucket}` - Create a bucket
- **DELETE** `/{bucket}` - Delete a bucket
- **HEAD** `/{bucket}` - Get bucket metadata
- **GET** `/{bucket}` - List objects in a bucket
- **HEAD** `/{bucket}/{key}` - Get object metadata
- **PUT** `/{bucket}/{key}` - Upload an object
- **GET** `/{bucket}/{key}` - Download an object
- **DELETE** `/{bucket}/{key}` - Delete an object
- **POST** `/{bucket}` - Delete multiple objects

## Actions

- list: List all buckets (GET /)
- update: Create a bucket (PUT /{bucket})
- delete: Delete a bucket (DELETE /{bucket})
- head_resource: Get bucket metadata (HEAD /{bucket})
- get_by_id: List objects in a bucket (GET /{bucket})
- get_object_metadata: Get object metadata (HEAD /{bucket}/{key})
- upload_object: Upload an object (PUT /{bucket}/{key})
- download_object: Download an object (GET /{bucket}/{key})
- delete_object: Delete an object (DELETE /{bucket}/{key})
- create_resource: Delete multiple objects (POST /{bucket})

## Fields

- `bucket`: string [REQUIRED] — Bucket
- `key`: string [REQUIRED for object operations] — API key or identifier

## Example Request Bodies

**Create Bucket:**
```json
{"bucket": "my-data-bucket"}
```

**Upload Object:**
```json
{"bucket": "my-data-bucket", "key": "documents/report-2024.pdf"}
```

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
