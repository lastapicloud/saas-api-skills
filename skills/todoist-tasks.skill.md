---
name: todoist-tasks
description: 'Manage Todoist tasks, projects, and labels. Use when the user mentions
  todoist, task, project, label.

  '
version: 1.0.0
skill_type: external
base_url_env: TODOIST_BASE_URL
auth_env_var: TODOIST_API_TOKEN
auth_type: bearer
triggers:
  - todoist
  - task
  - project
  - label
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires TODOIST_BASE_URL and TODOIST_API_TOKEN environment variables.
annotations:
  readOnlyHint: false
  destructiveHint: true
  idempotentHint: false
---

# Todoist-Tasks

Manage Todoist tasks, projects, and labels. Use when the user mentions todoist, task, project, label.


## API Endpoints

- **GET** `/rest/v2/tasks` - List tasks
- **GET** `/rest/v2/tasks/{taskId}` - Get a task
- **POST** `/rest/v2/tasks` - Create a task
- **POST** `/rest/v2/tasks/{taskId}` - Update a task
- **DELETE** `/rest/v2/tasks/{taskId}` - Delete a task
- **POST** `/rest/v2/tasks/{taskId}/close` - Close a task
- **GET** `/rest/v2/projects` - List projects
- **POST** `/rest/v2/projects` - Create a project
- **GET** `/rest/v2/labels` - List labels
- **GET** `/rest/v2/sections` - List sections

## Actions

- list: List tasks (GET /rest/v2/tasks)
- get_by_id: Get a task (GET /rest/v2/tasks/{taskId})
- create: Create a task (POST /rest/v2/tasks)
- add_tasks: Update a task (POST /rest/v2/tasks/{taskId})
- delete: Delete a task (DELETE /rest/v2/tasks/{taskId})
- close_task: Close a task (POST /rest/v2/tasks/{taskId}/close)
- list_projects: List projects (GET /rest/v2/projects)
- create_project: Create a project (POST /rest/v2/projects)
- list_labels: List labels (GET /rest/v2/labels)
- list_sections: List sections (GET /rest/v2/sections)

## Fields

- `content`: string [REQUIRED for create] — Content body
- `project_id`: string [OPTIONAL] — Project identifier
- `section_id`: string [OPTIONAL] — Section unique identifier
- `description`: string [OPTIONAL] — Human-readable description
- `priority`: integer [OPTIONAL] (1-4, 4 is highest) — Priority level
- `due_string`: string [OPTIONAL] (e.g., "tomorrow", "every monday") — Due String
- `labels`: array of strings [OPTIONAL] — Labels or categories

## Example Request Bodies

**Create Task:**
```json
{"content": "Review pull request #42", "description": "Check for security issues", "priority": 4, "due_string": "tomorrow", "labels": ["work", "urgent"]}
```

**Create Project:**
```json
{"name": "Q2 Sprint"}
```

## Response

**Task object:**
- `id`: string — Unique task identifier
- `name`: string — Task name or title
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
