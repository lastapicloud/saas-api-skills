---
name: cloudflare-r2-storage
description: Manage buckets and objects in Cloudflare R2 (S3-compatible). Use when
  the user mentions r2, cloudflare, bucket, object, storage, upload, download.
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
compatibility: Requires CLOUDFLARE_R2_BASE_URL and CLOUDFLARE_R2_ACCESS_KEY_ID environment
  variables.
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
- create: Create a bucket (PUT /{bucket})
- delete: Delete a bucket (DELETE /{bucket})
- head_bucket: Get bucket metadata (HEAD /{bucket})
- list_objects: List objects in a bucket (GET /{bucket})
- head_object: Get object metadata (HEAD /{bucket}/{key})
- upload: Upload an object (PUT /{bucket}/{key})
- download: Download an object (GET /{bucket}/{key})
- delete_object: Delete an object (DELETE /{bucket}/{key})
- delete_multiple: Delete multiple objects (POST /{bucket})
- list_uploads: List multipart uploads (GET /{bucket}?uploads)

## Fields

- `bucket`: string [REQUIRED for bucket/object actions] (bucket name)
- `key`: string [REQUIRED for object actions] (object key/path)
- `prefix`: string [OPTIONAL for list_objects] (filter by key prefix)
- `max-keys`: integer [OPTIONAL for list_objects] (max results, default 1000)
- `Content-Type`: string [OPTIONAL for upload_object] (MIME type of the object)

## Example Request Bodies

**List Objects (Query Params):**
Query parameter: `list-type=2&prefix=uploads/&max-keys=100`

**Upload Object:**
Binary body with `Content-Type` header set to the file's MIME type.

**Note:** Cloudflare R2 is fully S3-compatible. Use any S3 SDK by pointing the endpoint to `https://{account_id}.r2.cloudflarestorage.com`.
