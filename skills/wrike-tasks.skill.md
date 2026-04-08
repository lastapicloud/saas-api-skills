---
name: wrike-tasks
description: Manage Wrike tasks, folders, and projects. Use when the user mentions
  wrike, task, folder, project, workspace.
version: 1.0.0
skill_type: external
base_url_env: WRIKE_BASE_URL
auth_env_var: WRIKE_ACCESS_TOKEN
auth_type: bearer
triggers:
  - wrike
  - task
  - folder
  - project
  - workspace
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires WRIKE_BASE_URL and WRIKE_ACCESS_TOKEN environment variables.
---

# Wrike-Tasks

Manage Wrike tasks, folders, and projects. Use when the user mentions wrike, task, folder, project, workspace.

## API Endpoints

- **GET** `/api/v4/tasks` - List tasks
- **GET** `/api/v4/tasks/{taskId}` - Get a task
- **POST** `/api/v4/folders/{folderId}/tasks` - Create a task
- **PUT** `/api/v4/tasks/{taskId}` - Update a task
- **DELETE** `/api/v4/tasks/{taskId}` - Delete a task
- **GET** `/api/v4/folders` - List folders
- **POST** `/api/v4/folders/{folderId}/folders` - Create a folder
- **GET** `/api/v4/spaces` - List spaces
- **GET** `/api/v4/contacts` - List contacts
- **GET** `/api/v4/workflows` - List workflows

## Actions

- list: List tasks (GET /api/v4/tasks)
- get_by_id: Get a task (GET /api/v4/tasks/{taskId})
- create: Create a task (POST /api/v4/folders/{folderId}/tasks)
- update: Update a task (PUT /api/v4/tasks/{taskId})
- delete: Delete a task (DELETE /api/v4/tasks/{taskId})
- list_folders: List folders (GET /api/v4/folders)
- create_folders: Create a folder (POST /api/v4/folders/{folderId}/folders)
- list_spaces: List spaces (GET /api/v4/spaces)
- list_contacts: List contacts (GET /api/v4/contacts)
- list_workflows: List workflows (GET /api/v4/workflows)

## Fields

- `title`: string [REQUIRED for create]
- `description`: string [OPTIONAL]
- `status`: string [OPTIONAL] (e.g., "Active", "Completed", "Deferred", "Cancelled")
- `importance`: string [OPTIONAL] (e.g., "High", "Normal", "Low")
- `dates`: object [OPTIONAL] (start, due, duration)
- `responsibles`: array of strings (contact IDs) [OPTIONAL]

## Example Request Bodies

**Create Task:**
```json
{"title": "Design new landing page", "description": "Create mockups for the Q2 campaign", "status": "Active", "importance": "High", "dates": {"due": "2026-04-15"}}
```

**Create Folder:**
```json
{"title": "Q2 Marketing"}
```
