---
name: azure-blob-storage
description: Manage blob containers and objects via Azure Blob Storage. Use when the
  user mentions azure blob, blob storage, azure storage, container, blob, upload.
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
- create: Create a container (PUT /{container}?restype=container)
- delete: Delete a container (DELETE /{container}?restype=container)
- head_container: Get container properties (HEAD /{container}?restype=container)
- list_blobs: List blobs in container (GET /{container}?restype=container&comp=list)
- upload: Upload a blob (PUT /{container}/{blob})
- download: Download a blob (GET /{container}/{blob})
- delete_blob: Delete a blob (DELETE /{container}/{blob})
- head_blob: Get blob properties (HEAD /{container}/{blob})
- update_blob: Update blob properties (PATCH /{container}/{blob})
- copy_blob: Copy a blob (PUT /{container}/{blob}?comp=copy)
- lease_blob: Lease a blob (POST /{container}/{blob}?comp=Lease)

## Fields

- `container`: string [REQUIRED]
- `blob`: string [REQUIRED for blob operations]

## Example Request Bodies

**Create Container:**
```json
{"container": "project-backups"}
```

**Upload Blob:**
```json
{"container": "project-backups", "blob": "db-dump-2026-04-01.sql.gz"}
```
