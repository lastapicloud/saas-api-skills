---
name: google-drive
description: Manage files and folders in Google Drive. Use when the user mentions
  drive, google drive, file, upload, download, folder, storage.
version: 1.0.0
skill_type: external
base_url_env: GOOGLE_DRIVE_BASE_URL
auth_env_var: GOOGLE_API_TOKEN
auth_type: bearer
triggers:
  - drive
  - google drive
  - file
  - upload
  - download
  - folder
  - storage
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires GOOGLE_DRIVE_BASE_URL and GOOGLE_API_TOKEN environment variables.
---

# Google-Drive

Manage files and folders in Google Drive. Use when the user mentions drive, google drive, file, upload, download, folder, storage.

## API Endpoints

- **GET** `/files` - List files
- **GET** `/files/{fileId}` - Get file metadata
- **POST** `/files` - Upload a file or create a folder
- **POST** `/files` - Create a folder (with mimeType application/vnd.google-apps.folder)
- **GET** `/files` - Search files (with q parameter)
- **POST** `/files/{fileId}/permissions` - Share a file
- **DELETE** `/files/{fileId}` - Delete a file
- **GET** `/drive/v3/files/{fileId}/accessproposals/{proposalId}`
- **GET** `/drive/v3/files/{fileId}/accessproposals`
- **POST** `/drive/v3/files/{fileId}/accessproposals/{proposalId}:resolve`
- **GET** `/drive/v3/files/{fileId}/approvals/{approvalId}`
- **GET** `/drive/v3/files/{fileId}/approvals`
- **GET** `/drive/v3/apps/{appId}`
- **GET** `/drive/v3/apps`
- **GET** `/drive/v3/changes/startPageToken`

## Actions

- list: List files (GET /files)
- get_by_id: Get file metadata (GET /files/{fileId})
- create: Upload a file or create a folder (POST /files)
- create_files: Create a folder (with mimeType application/vnd.google-apps.folder) (POST /files)
- list_files: Search files (with q parameter) (GET /files)
- create_permissions: Share a file (POST /files/{fileId}/permissions)
- delete: Delete a file (DELETE /files/{fileId})
- get_by_id_accessproposals: GET /drive/v3/files/{fileId}/accessproposals/{proposalId} (GET /drive/v3/files/{fileId}/accessproposals/{proposalId})
- list_accessproposals: GET /drive/v3/files/{fileId}/accessproposals (GET /drive/v3/files/{fileId}/accessproposals)
- create_accessproposals: POST /drive/v3/files/{fileId}/accessproposals/{proposalId}:resolve (POST /drive/v3/files/{fileId}/accessproposals/{proposalId}:resolve)
- get_by_id_approvals: GET /drive/v3/files/{fileId}/approvals/{approvalId} (GET /drive/v3/files/{fileId}/approvals/{approvalId})
- list_approvals: GET /drive/v3/files/{fileId}/approvals (GET /drive/v3/files/{fileId}/approvals)
- get_by_id_apps: GET /drive/v3/apps/{appId} (GET /drive/v3/apps/{appId})
- list_apps: GET /drive/v3/apps (GET /drive/v3/apps)
- list_startpagetoken: GET /drive/v3/changes/startPageToken (GET /drive/v3/changes/startPageToken)

## Fields

- `fileId`: string [REQUIRED for get_file, share_file, delete_file] (the file ID)
- `name`: string [REQUIRED for upload_file, create_folder] (file or folder name)
- `mimeType`: string [OPTIONAL] (MIME type; use application/vnd.google-apps.folder for folders)
- `parents`: array of strings [OPTIONAL] (parent folder IDs)
- `q`: string [REQUIRED for search_files] (search query, e.g. "name contains 'report'")
- `role`: string [REQUIRED for share_file] (reader, writer, commenter, owner)
- `type`: string [REQUIRED for share_file] (user, group, domain, anyone)
- `emailAddress`: string [OPTIONAL for share_file] (email of the user to share with)

## Example Request Bodies

**Create Folder:**
```json
{"name": "Project Files", "mimeType": "application/vnd.google-apps.folder"}
```

**Share File:**
```json
{"role": "reader", "type": "user", "emailAddress": "user@example.com"}
```

**Search Files (Query Params):**
Query parameter: `q=name+contains+'report'&fields=files(id,name,mimeType)`
