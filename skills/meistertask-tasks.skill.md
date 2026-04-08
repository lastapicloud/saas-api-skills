---
name: meistertask-tasks
description: Manage projects and tasks via MeisterTask. Use when the user mentions
  meistertask, task, project, kanban, board.
version: 1.0.0
skill_type: external
base_url_env: MEISTERTASK_BASE_URL
auth_env_var: MEISTERTASK_API_TOKEN
auth_type: bearer
triggers:
  - meistertask
  - task
  - project
  - kanban
  - board
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires MEISTERTASK_BASE_URL and MEISTERTASK_API_TOKEN environment
  variables.
---

# Meistertask-Tasks

Manage projects and tasks via MeisterTask. Use when the user mentions meistertask, task, project, kanban, board.

## API Endpoints

- **GET** `/api/v2/projects` - List projects
- **POST** `/api/v2/projects` - Create project
- **GET** `/api/v2/projects/{projectId}` - Get project
- **GET** `/api/v2/projects/{projectId}/tasks` - List tasks
- **POST** `/api/v2/projects/{projectId}/tasks` - Create task
- **GET** `/api/v2/tasks/{taskId}` - Get task
- **PUT** `/api/v2/tasks/{taskId}` - Update task
- **DELETE** `/api/v2/tasks/{taskId}` - Delete task

## Actions

- list: List projects (GET /api/v2/projects)
- create: Create project (POST /api/v2/projects)
- get_by_id: Get project (GET /api/v2/projects/{projectId})
- list_tasks: List tasks (GET /api/v2/projects/{projectId}/tasks)
- create_tasks: Create task (POST /api/v2/projects/{projectId}/tasks)
- get_by_id_tasks: Get task (GET /api/v2/tasks/{taskId})
- update: Update task (PUT /api/v2/tasks/{taskId})
- delete: Delete task (DELETE /api/v2/tasks/{taskId})

## Fields

- `name`: string [REQUIRED for create]
- `notes`: string [OPTIONAL]
- `section_id`: integer [OPTIONAL]

## Example Request Bodies

**Create Project:**
```json
{"name": "Website Redesign", "notes": "Complete overhaul of the marketing website"}
```

**Create Task:**
```json
{"name": "Update homepage hero section", "section_id": 456, "notes": "Replace current banner with new design"}
```
