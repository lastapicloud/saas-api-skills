---
name: mural-collaboration
description: Visual collaboration via MURAL. Use when the user mentions mural, visual collaboration, whiteboard, design thinking, workshop, diagram.
version: 1.0.0
skill_type: external
base_url_env: MURAL_BASE_URL
auth_env_var: MURAL_CLIENT_ID
auth_type: bearer
triggers:
  - mural
  - visual collaboration
  - whiteboard
  - design thinking
  - workshop
license: Proprietary
metadata:
  author: lastapi
  version: 1.0.0
  documentation: https://developers.mural.co/
---

# Mural-Collaboration

Visual collaboration via MURAL. Use when the user mentions mural, visual collaboration, whiteboard, design thinking, workshop, diagram.

## API Endpoints

- **GET** `/murals` - List murals
- **POST** `/murals` - Create mural
- **GET** `/murals/{muralId}` - Get mural
- **PUT** `/murals/{muralId}` - Update mural
- **DELETE** `/murals/{muralId}` - Delete mural
- **GET** `/murals/{muralId}/contents` - Get mural contents
- **POST** `/murals/{muralId}/contents` - Add content to mural
- **GET** `/murals/{muralId}/members` - List members
- **POST** `/murals/{muralId}/members` - Add member
- **DELETE** `/murals/{muralId}/members/{userId}` - Remove member

## Actions

- list_murals: List murals (GET /murals)
- create_mural: Create mural (POST /murals)
- get_mural: Get mural (GET /murals/{muralId})
- update_mural: Update mural (PUT /murals/{muralId})
- delete_mural: Delete mural (DELETE /murals/{muralId})
- get_contents: Get mural contents (GET /murals/{muralId}/contents)
- add_content: Add content (POST /murals/{muralId}/contents)
- list_members: List members (GET /murals/{muralId}/members)
- add_member: Add member (POST /murals/{muralId}/members)
- remove_member: Remove member (DELETE /murals/{muralId}/members/{userId})

## Fields

- `title`: string [REQUIRED for create] - Mural title
- `templateId`: string [OPTIONAL] - Template ID
- `workspaceId`: string [REQUIRED] - Workspace ID
- `contents`: object [OPTIONAL] - Mural contents
- `role`: string [OPTIONAL] - Member role (viewer, editor)

## Example Request Bodies

**Create Mural:**
```json
{"title": "Sprint Planning", "workspaceId": "WORKSPACE_ID"}
```

**Add Member:**
```json
{"userId": "USER_ID", "role": "editor"}
```
