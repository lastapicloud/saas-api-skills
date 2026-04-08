---
name: webwork-time
description: Time tracking and project management via WebWork. Use when the user mentions webwork, time tracking, time tracker, employee tracking, project time.
version: 1.0.0
skill_type: external
base_url_env: WEBWORK_BASE_URL
auth_env_var: WEBWORK_API_KEY
auth_type: bearer
triggers:
  - webwork
  - time tracking
  - time tracker
  - employee tracking
  - project time
license: Proprietary
metadata:
  author: lastapi
  version: 1.0.0
  documentation: https://api-docs.webwork-tracker.com/
---

# Webwork-Time

Time tracking and project management via WebWork. Use when the user mentions webwork, time tracking, time tracker, employee tracking, project time.

## API Endpoints

- **GET** `/api/projects` - List projects
- **POST** `/api/projects` - Create project
- **GET** `/api/projects/{id}` - Get project
- **PUT** `/api/projects/{id}` - Update project
- **DELETE** `/api/projects/{id}` - Delete project
- **GET** `/api/tasks` - List tasks
- **POST** `/api/tasks` - Create task
- **GET** `/api/tasks/{id}` - Get task
- **PUT** `/api/tasks/{id}` - Update task
- **GET** `/api/time-entries` - List time entries
- **POST** `/api/time-entries` - Create time entry
- **GET** `/api/time-entries/{id}` - Get time entry
- **PUT** `/api/time-entries/{id}` - Update time entry
- **GET** `/api/users` - List users
- **GET** `/api/users/{id}` - Get user

## Actions

- list_projects: List projects (GET /api/projects)
- create_project: Create project (POST /api/projects)
- get_project: Get project (GET /api/projects/{id})
- update_project: Update project (PUT /api/projects/{id})
- delete_project: Delete project (DELETE /api/projects/{id})
- list_tasks: List tasks (GET /api/tasks)
- create_task: Create task (POST /api/tasks)
- get_task: Get task (GET /api/tasks/{id})
- update_task: Update task (PUT /api/tasks/{id})
- list_entries: List time entries (GET /api/time-entries)
- create_entry: Create time entry (POST /api/time-entries)
- get_entry: Get time entry (GET /api/time-entries/{id})
- update_entry: Update time entry (PUT /api/time-entries/{id})
- list_users: List users (GET /api/users)
- get_user: Get user (GET /api/users/{id})

## Fields

- `name`: string [REQUIRED for create] - Project/task name
- `description`: string [OPTIONAL] - Description
- `status`: string [OPTIONAL] - Status (active, paused, completed)
- `userId`: integer [REQUIRED for entry] - User ID
- `projectId`: integer [REQUIRED for entry] - Project ID
- `start`: string [REQUIRED for entry] - Start time (ISO 8601)
- `duration`: integer [OPTIONAL] - Duration in minutes

## Example Request Bodies

**Create Project:**
```json
{"name": "Website Redesign", "description": "Main company website", "status": "active"}
```

**Create Time Entry:**
```json
{"userId": 1, "projectId": 1, "start": "2024-01-15T09:00:00Z", "duration": 120}
```

**Create Task:**
```json
{"projectId": 1, "name": "Design homepage", "status": "active"}
```
