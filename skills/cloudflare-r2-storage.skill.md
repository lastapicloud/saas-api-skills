---
name: cloudflare-r2-storage
description: 'Manage buckets and objects in Cloudflare R2 (S3-compatible). Use when
  the user mentions r2, cloudflare, bucket, object, storage, upload, download.

  '
version: 1.0.0
skill_type: external
base_url_env: CLOUDFLARE_R2_BASE_URL
auth_env_var: CLOUDFLARE_R2_ACCESS_KEY_ID
auth_type: aws_sigv4
triggers:
  - r2
  - cloudflare
  - bucket
  - object
  - storage
  - upload
  - download
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: 'Requires CLOUDFLARE_R2_BASE_URL and CLOUDFLARE_R2_ACCESS_KEY_ID environment
  variables.

  '
annotations:
  readOnlyHint: false
  destructiveHint: true
  idempotentHint: false
---

# Cloudflare-R2-Storage

Manage buckets and objects in Cloudflare R2 (S3-compatible). Use when the user mentions r2, cloudflare, bucket, object, storage, upload, download.


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
- **POST** `/{bucket}` - Delete multiple objects (batch delete)
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
- create_resource: Delete multiple objects (batch delete) (POST /{bucket})
- list_multipart_uploads: List multipart uploads (GET /{bucket}?uploads)

## Fields

- `bucket`: string [REQUIRED for bucket/object actions] (bucket name) — Bucket
- `key`: string [REQUIRED for object actions] (object key/path) — API key or identifier
- `prefix`: string [OPTIONAL for list_objects] (filter by key prefix) — Prefix
- `max-keys`: integer [OPTIONAL for list_objects] (max results, default 1000) — Max Keys value
- `Content-Type`: string [OPTIONAL for upload_object] (MIME type of the object) — Content- resource type

## Example Request Bodies

**List Objects (Query Params):**
Query parameter: `list-type=2&prefix=uploads/&max-keys=100`

**Upload Object:**
Binary body with `Content-Type` header set to the file's MIME type.

**Note:** Cloudflare R2 is fully S3-compatible. Use any S3 SDK by pointing the endpoint to `https://{account_id}.r2.cloudflarestorage.com`.

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
