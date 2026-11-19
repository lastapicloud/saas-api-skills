---
name: azure-blob-storage
description: 'Manage blob containers and objects via Azure Blob Storage. Use when
  the user mentions azure blob, blob storage, azure storage, container, blob, upload.

  '
version: 1.0.0
skill_type: external
base_url_env: AZURE_BLOB_BASE_URL
auth_env_var: AZURE_BLOB_ACCESS_KEY
auth_type: header
triggers:
  - azure blob
  - blob storage
  - azure storage
  - container
  - blob
  - upload
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires AZURE_BLOB_BASE_URL and AZURE_BLOB_ACCESS_KEY environment
  variables.
annotations:
  readOnlyHint: false
  destructiveHint: true
  idempotentHint: false
---

# Azure-Blob-Storage

Manage blob containers and objects via Azure Blob Storage. Use when the user mentions azure blob, blob storage, azure storage, container, blob, upload.


## API Endpoints

- **GET** `/?comp=list` - List containers
- **PUT** `/{container}?restype=container` - Create a container
- **DELETE** `/{container}?restype=container` - Delete a container
- **HEAD** `/{container}?restype=container` - Get container properties
- **GET** `/{container}?restype=container&comp=list` - List blobs in container
- **PUT** `/{container}/{blob}` - Upload a blob
- **GET** `/{container}/{blob}` - Download a blob
- **DELETE** `/{container}/{blob}` - Delete a blob
- **HEAD** `/{container}/{blob}` - Get blob properties
- **PATCH** `/{container}/{blob}` - Update blob properties
- **PUT** `/{container}/{blob}?comp=copy` - Copy a blob
- **POST** `/{container}/{blob}?comp=Lease` - Lease a blob

## Actions

- list: List containers (GET /?comp=list)
- update_resource: Create a container (PUT /{container}?restype=container)
- delete_resource: Delete a container (DELETE /{container}?restype=container)
- head_resource: Get container properties (HEAD /{container}?restype=container)
- list_blobs_container: List blobs in container (GET /{container}?restype=container&comp=list)
- update: Upload a blob (PUT /{container}/{blob})
- get_by_id: Download a blob (GET /{container}/{blob})
- delete: Delete a blob (DELETE /{container}/{blob})
- get_blob_properties: Get blob properties (HEAD /{container}/{blob})
- update_blob_properties: Update blob properties (PATCH /{container}/{blob})
- copy_blob: Copy a blob (PUT /{container}/{blob}?comp=copy)
- create: Lease a blob (POST /{container}/{blob}?comp=Lease)

## Fields

- `container`: string [REQUIRED] — Container
- `blob`: string [REQUIRED for blob operations] — Blob

## Example Request Bodies

**Create Container:**
```json
{"container": "project-backups"}
```

**Upload Blob:**
```json
{"container": "project-backups", "blob": "db-dump-2026-04-01.sql.gz"}
```

## Response

**?Comp=List object:**
- `id`: string — Unique ?comp=list identifier
- `name`: string — ?Comp=List name or title
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
