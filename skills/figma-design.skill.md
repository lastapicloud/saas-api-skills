---
name: figma-design
description: Access Figma files, components, and comments. Use when the user mentions
  figma, design, file, component, prototype.
version: 1.0.0
skill_type: external
base_url_env: FIGMA_BASE_URL
auth_env_var: FIGMA_ACCESS_TOKEN
auth_type: bearer
triggers:
  - figma
  - design
  - file
  - component
  - prototype
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires FIGMA_BASE_URL and FIGMA_ACCESS_TOKEN environment variables.
---

# Figma-Design

Access Figma files, components, and comments. Use when the user mentions figma, design, file, component, prototype.

## API Endpoints

- **GET** `/v1/files/{fileKey}` - Get a file
- **GET** `/v1/files/{fileKey}/nodes` - Get file nodes
- **GET** `/v1/files/{fileKey}/images` - Export images
- **GET** `/v1/files/{fileKey}/comments` - List comments
- **POST** `/v1/files/{fileKey}/comments` - Add a comment
- **GET** `/v1/files/{fileKey}/components` - List components
- **GET** `/v1/files/{fileKey}/styles` - List styles
- **GET** `/v1/teams/{teamId}/projects` - List team projects
- **GET** `/v1/projects/{projectId}/files` - List project files
- **GET** `/v1/me` - Get current user
- **GET** `/v2/webhooks` - Get webhooks by context or plan
- **POST** `/v2/webhooks` - Create a webhook
- **GET** `/v1/files/{file_key}` - Get file JSON
- **DELETE** `/v1/files/{file_key}/comments/{comment_id}` - Delete a comment
- **POST** `/v1/files/{file_key}/comments` - Add a comment to a file

## Actions

- get_by_id: Get a file (GET /v1/files/{fileKey})
- list: Get file nodes (GET /v1/files/{fileKey}/nodes)
- list_images: Export images (GET /v1/files/{fileKey}/images)
- list_comments: List comments (GET /v1/files/{fileKey}/comments)
- create: Add a comment (POST /v1/files/{fileKey}/comments)
- list_components: List components (GET /v1/files/{fileKey}/components)
- list_styles: List styles (GET /v1/files/{fileKey}/styles)
- list_projects: List team projects (GET /v1/teams/{teamId}/projects)
- list_files: List project files (GET /v1/projects/{projectId}/files)
- list_me: Get current user (GET /v1/me)
- list_webhooks: Get webhooks by context or plan (GET /v2/webhooks)
- create_webhooks: Create a webhook (POST /v2/webhooks)
- get_by_id_files: Get file JSON (GET /v1/files/{file_key})
- delete: Delete a comment (DELETE /v1/files/{file_key}/comments/{comment_id})
- create_comments: Add a comment to a file (POST /v1/files/{file_key}/comments)

## Fields

- `message`: string [REQUIRED for add comment]
- `client_meta`: object [OPTIONAL for comment] with `x`, `y` (position)
- `ids`: string [OPTIONAL for nodes/images] (comma-separated node IDs)
- `format`: string [OPTIONAL for export] ("jpg", "png", "svg", "pdf")
- `scale`: number [OPTIONAL for export]

## Example Request Bodies

**Add Comment:**
```json
{"message": "The padding on the header looks off. Can we increase it to 24px?", "client_meta": {"x": 150.0, "y": 320.0}}
```

**Export Images (query parameters):**
```json
{"ids": "1:2,3:4", "format": "png", "scale": 2}
```
