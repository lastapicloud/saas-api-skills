---
name: wasabi-storage
description: 'Manage buckets and objects via Wasabi cloud storage. Use when the user
  mentions wasabi, s3, bucket, object, storage, cloud storage.

  '
version: 1.0.0
skill_type: external
base_url_env: WASABI_BASE_URL
auth_env_var: WASABI_ACCESS_KEY_ID
auth_user_env: WASABI_SECRET_ACCESS_KEY
auth_type: header
triggers:
  - wasabi
  - s3
  - bucket
  - object
  - storage
  - cloud storage
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires WASABI_BASE_URL and WASABI_ACCESS_KEY_ID environment variables.
annotations:
  readOnlyHint: false
  destructiveHint: true
  idempotentHint: false
---

# Wasabi-Storage

Manage buckets and objects via Wasabi cloud storage. Use when the user mentions wasabi, s3, bucket, object, storage, cloud storage.


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
- **GET** `/{bucket}?uploads` - List multipart uploads

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
- list_multipart_uploads: List multipart uploads (GET /{bucket}?uploads)

## Fields

- `bucket`: string [REQUIRED] — Bucket
- `key`: string [REQUIRED for object operations] — API key or identifier

## Example Request Bodies

**Create Bucket:**
```json
{"bucket": "my-data-backups"}
```

**Upload Object:**
```json
{"bucket": "my-data-backups", "key": "reports/2026/q1-summary.pdf"}

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
