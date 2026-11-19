---
name: imagekit-media
description: 'Upload and transform images via ImageKit. Use when the user mentions
  imagekit, image, upload, transform, media, cdn.

  '
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
annotations:
  readOnlyHint: false
  destructiveHint: true
  idempotentHint: false
---

# Imagekit-Media

Upload and transform images via ImageKit. Use when the user mentions imagekit, image, upload, transform, media, cdn.


## API Endpoints

- **GET** `/v1/customMetadataFields` - This API returns the array of created custom metadata field objects
- **POST** `/v1/customMetadataFields` - This API creates a new custom metadata field
- **PATCH** `/v1/customMetadataFields/{id}` - This API updates the label or schema of an existing custom metadata field
- **DELETE** `/v1/customMetadataFields/{id}` - This API deletes a custom metadata field
- **GET** `/v1/files` - This API can list all the uploaded files and folders in your ImageKit
- **POST** `/v1/files/copy` - This will copy a file from one folder to another
- **DELETE** `/v1/files/{fileId}` - This API deletes the file and all its file versions permanently
- **PUT** `/v1/files/rename` - You can rename an already existing file in the media library using rename file API
- **PATCH** `/v1/files/{fileId}/details` - This API updates the details or attributes of the current version of the file
- **POST** `/v1/bulkJobs/copyFolder` - This will copy one folder into another
- **GET** `/v1/bulkJobs/{jobId}` - This API returns the status of a bulk job like copy and move folder operations
- **POST** `/v1/folder` - This will create a new folder
- **DELETE** `/v1/folder` - This will delete a folder and all its contents permanently
- **GET** `/v1/accounts/usage` - Get the account usage information between two dates
- **POST** `/api/v1/files/upload` - ImageKit

## Actions

- list: This API returns the array of created custom metadata field objects (GET /v1/customMetadataFields)
- create: This API creates a new custom metadata field (POST /v1/customMetadataFields)
- update: This API updates the label or schema of an existing custom metadata field (PATCH /v1/customMetadataFields/{id})
- delete: This API deletes a custom metadata field (DELETE /v1/customMetadataFields/{id})
- get_this_api_can_list: This API can list all the uploaded files and folders in your ImageKit (GET /v1/files)
- create_this_will_copy_file: This will copy a file from one folder to another (POST /v1/files/copy)
- delete_this_api_deletes_file: This API deletes the file and all its file versions permanently (DELETE /v1/files/{fileId})
- put_rename: You can rename an already existing file in the media library using rename file A (PUT /v1/files/rename)
- patch_details: This API updates the details or attributes of the current version of the file (PATCH /v1/files/{fileId}/details)
- create_this_will_copy_one: This will copy one folder into another (POST /v1/bulkJobs/copyFolder)
- get_by_id: This API returns the status of a bulk job like copy and move folder operations (GET /v1/bulkJobs/{jobId})
- create_this_will_create_new: This will create a new folder (POST /v1/folder)
- delete_folder: This will delete a folder and all its contents permanently (DELETE /v1/folder)
- get_account_usage_information: Get the account usage information between two dates (GET /v1/accounts/usage)
- create_imagekit: ImageKit (POST /api/v1/files/upload)

## Fields

- `file`: string [REQUIRED for upload] (base64 or URL) — File
- `fileName`: string [REQUIRED for upload] — File display name
- `folder`: string [OPTIONAL] — Folder

## Example Request Bodies

**Upload File:**
```json
{"file": "https://example.com/images/photo.jpg", "fileName": "photo.jpg", "folder": "/uploads/2024"}
```

**Move File:**
```json
{"sourceFilePath": "/uploads/2024/photo.jpg", "destinationPath": "/archive/2024/"}
```

## Response

**Custommetadatafield object:**
- `id`: string — Unique custommetadatafield identifier
- `name`: string — Custommetadatafield name or title
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
