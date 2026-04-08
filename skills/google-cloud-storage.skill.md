---
name: google-cloud-storage
description: Manage buckets and objects via Google Cloud Storage. Use when the user
  mentions google cloud storage, gcs, bucket, object, cloud storage.
version: 1.0.0
skill_type: external
base_url_env: GOOGLE_CLOUD_STORAGE_BASE_URL
auth_env_var: GOOGLE_API_TOKEN
auth_type: bearer
triggers:
  - google cloud storage
  - gcs
  - bucket
  - object
  - cloud storage
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires GOOGLE_CLOUD_STORAGE_BASE_URL and GOOGLE_API_TOKEN environment
  variables.
---

# Google-Cloud-Storage

Manage buckets and objects via Google Cloud Storage. Use when the user mentions google cloud storage, gcs, bucket, object, cloud storage.

## API Endpoints

- **GET** `/storage/v1/b` - List buckets
- **POST** `/storage/v1/b` - Create bucket
- **GET** `/storage/v1/b/{bucket}` - Get bucket
- **DELETE** `/storage/v1/b/{bucket}` - Delete bucket
- **GET** `/storage/v1/b/{bucket}/o` - List objects
- **GET** `/storage/v1/b/{bucket}/o/{object}` - Get object metadata
- **DELETE** `/storage/v1/b/{bucket}/o/{object}` - Delete object
- **POST** `/upload/storage/v1/b/{bucket}/o` - Upload object

## Actions

- list: List buckets (GET /storage/v1/b)
- create: Create bucket (POST /storage/v1/b)
- get_by_id: Get bucket (GET /storage/v1/b/{bucket})
- delete: Delete bucket (DELETE /storage/v1/b/{bucket})
- list_o: List objects (GET /storage/v1/b/{bucket}/o)
- get_by_id_o: Get object metadata (GET /storage/v1/b/{bucket}/o/{object})
- delete_o: Delete object (DELETE /storage/v1/b/{bucket}/o/{object})
- create_o: Upload object (POST /upload/storage/v1/b/{bucket}/o)

## Fields

- `name`: string [REQUIRED for create_bucket]
- `project`: string [REQUIRED]
- `prefix`: string [OPTIONAL for list]

## Example Request Bodies

**Create Bucket:**
```json
{"name": "my-new-bucket", "project": "my-gcp-project-123"}
```

**Upload Object:**
```json
{"name": "documents/report.pdf", "contentType": "application/pdf"}
```
