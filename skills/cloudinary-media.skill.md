---
name: cloudinary-media
description: Upload and manage images, videos, and media assets via the Cloudinary
  API. Use when the user mentions cloudinary, image, upload, media, video, transform.
version: 1.0.0
skill_type: external
base_url_env: CLOUDINARY_BASE_URL
auth_env_var: CLOUDINARY_API_SECRET
auth_user_env: CLOUDINARY_API_KEY
auth_type: basic
triggers:
  - cloudinary
  - image
  - upload
  - media
  - video
  - transform
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires CLOUDINARY_BASE_URL and CLOUDINARY_API_SECRET environment
  variables.
---

# Cloudinary-Media

Upload and manage images, videos, and media assets via the Cloudinary API. Use when the user mentions cloudinary, image, upload, media, video, transform.

## API Endpoints

- **POST** `/image/upload` - Upload an image
- **GET** `/resources/image` - List image resources
- **GET** `/resources/image/upload/{public_id}` - Get resource details
- **DELETE** `/resources/image/upload` - Delete a resource
- **POST** `/folders/{folder_path}` - Create a folder
- **GET** `/usage`
- **GET** `/config`
- **GET** `/folders`
- **GET** `/folders/:folder`
- **GET** `/folders/search`
- **POST** `/folders/:folder`
- **PUT** `/folders/:folder`
- **DELETE** `/folders/:folder`
- **GET** `/metadata_fields`
- **GET** `/metadata_fields/:external_id`

## Actions

- create: Upload an image (POST /image/upload)
- list: List image resources (GET /resources/image)
- get_by_id: Get resource details (GET /resources/image/upload/{public_id})
- delete_upload: Delete a resource (DELETE /resources/image/upload)
- create_folders: Create a folder (POST /folders/{folder_path})
- list_usage: GET /usage (GET /usage)
- list_config: GET /config (GET /config)
- list_folders: GET /folders (GET /folders)
- list_folder: GET /folders/:folder (GET /folders/:folder)
- search: GET /folders/search (GET /folders/search)
- create_folder: POST /folders/:folder (POST /folders/:folder)
- put_:folder: PUT /folders/:folder (PUT /folders/:folder)
- delete_:folder: DELETE /folders/:folder (DELETE /folders/:folder)
- list_metadata_fields: GET /metadata_fields (GET /metadata_fields)
- list_external_id: GET /metadata_fields/:external_id (GET /metadata_fields/:external_id)

## Fields

- `file`: string [REQUIRED for upload_image] (file URL or base64 data)
- `public_id`: string [OPTIONAL for upload_image, REQUIRED for get_resource] (resource public ID)
- `folder`: string [OPTIONAL for upload_image] (target folder)
- `folder_path`: string [REQUIRED for create_folder] (folder path to create)
- `resource_type`: string [OPTIONAL] (resource type: image, video, raw)
- `public_ids`: array [REQUIRED for delete_resource] (list of public IDs to delete)
- `max_results`: integer [OPTIONAL for list_resources] (max resources to return)

## Example Request Bodies

**Upload Image:**
```json
{"file": "https://example.com/image.jpg", "public_id": "test-image", "folder": "test"}
```

**Delete Resource (Query Params):**
Query parameter: `public_ids[]=test-image&public_ids[]=test-image-2`
