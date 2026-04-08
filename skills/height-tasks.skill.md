---
name: height-tasks
description: Manage tasks and lists via Height. Use when the user mentions height,
  task, list, project, workspace.
version: 1.0.0
skill_type: external
base_url_env: HEIGHT_BASE_URL
auth_env_var: HEIGHT_API_KEY
auth_type: bearer
triggers:
  - height
  - task
  - list
  - project
  - workspace
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires HEIGHT_BASE_URL and HEIGHT_API_KEY environment variables.
---

# Height-Tasks

Manage tasks and lists via Height. Use when the user mentions height, task, list, project, workspace.

## API Endpoints

- **GET** `/tasks` - List tasks
- **POST** `/tasks` - Create task
- **GET** `/tasks/{taskId}` - Get task
- **PATCH** `/tasks/{taskId}` - Update task
- **GET** `/lists` - List lists
- **POST** `/lists` - Create list
- **GET** `/workspace` - Get workspace
- **POST** `/activities` - Create activity

## Actions

- list: List tasks (GET /tasks)
- create: Create task (POST /tasks)
- get_by_id: Get task (GET /tasks/{taskId})
- update: Update task (PATCH /tasks/{taskId})
- list_lists: List lists (GET /lists)
- create_lists: Create list (POST /lists)
- list_workspace: Get workspace (GET /workspace)
- create_activities: Create activity (POST /activities)

## Fields

- `name`: string [REQUIRED for create]
- `listIds`: array [REQUIRED for create]
- `description`: string [OPTIONAL]
- `status`: string [OPTIONAL]

## Example Request Bodies

**Create Task:**
```json
{"name": "Implement login page", "listIds": ["list-abc123"], "description": "Build the user login page with OAuth support", "status": "backLog"}
```

**Create List:**
```json
{"name": "Sprint 14", "description": "Tasks for the current sprint"}
```
