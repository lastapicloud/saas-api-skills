---
name: backblaze-b2-storage
description: Manage buckets and files via Backblaze B2 cloud storage. Use when the
  user mentions backblaze, b2, cloud storage, bucket, file, backup.
version: 1.0.0
skill_type: external
base_url_env: BACKBLAZE_B2_BASE_URL
auth_env_var: BACKBLAZE_B2_APPLICATION_KEY
auth_user_env: BACKBLAZE_B2_KEY_ID
auth_type: bearer
triggers:
  - backblaze
  - b2
  - cloud storage
  - bucket
  - file
  - backup
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires BACKBLAZE_B2_BASE_URL and BACKBLAZE_B2_APPLICATION_KEY environment
  variables.
---

# Backblaze-B2-Storage

Manage buckets and files via Backblaze B2 cloud storage. Use when the user mentions backblaze, b2, cloud storage, bucket, file, backup.

## API Endpoints

- **POST** `/b2api/v3/b2_list_buckets` - List buckets
- **POST** `/b2api/v3/b2_create_bucket` - Create a bucket
- **POST** `/b2api/v3/b2_delete_bucket` - Delete a bucket
- **POST** `/b2api/v3/b2_list_file_names` - List files in a bucket
- **POST** `/b2api/v3/b2_get_upload_url` - Get upload URL
- **POST** `/b2api/v3/b2_delete_file_version` - Delete a file
- **POST** `/b2api/v3/b2_download_file_by_id` - Download a file by ID
- **POST** `/b2api/v3/b2_authorize_account` - Authorize account

## Actions

- create: List buckets (POST /b2api/v3/b2_list_buckets)
- create_b2_create_bucket: Create a bucket (POST /b2api/v3/b2_create_bucket)
- create_b2_delete_bucket: Delete a bucket (POST /b2api/v3/b2_delete_bucket)
- create_b2_list_file_names: List files in a bucket (POST /b2api/v3/b2_list_file_names)
- create_b2_get_upload_url: Get upload URL (POST /b2api/v3/b2_get_upload_url)
- create_b2_delete_file_version: Delete a file (POST /b2api/v3/b2_delete_file_version)
- create_b2_download_file_by_id: Download a file by ID (POST /b2api/v3/b2_download_file_by_id)
- create_b2_authorize_account: Authorize account (POST /b2api/v3/b2_authorize_account)

## Fields

- `bucketName`: string [REQUIRED for create_bucket]
- `bucketType`: string [REQUIRED for create_bucket] (allPublic or allPrivate)
- `bucketId`: string [REQUIRED for list/delete]

## Example Request Bodies

**Create Bucket:**
```json
{"bucketName": "app-media-assets", "bucketType": "allPrivate", "accountId": "your-account-id"}
```

**List Files in Bucket:**
```json
{"bucketId": "b2f1a7c8d9e0", "maxFileCount": 100}
```
