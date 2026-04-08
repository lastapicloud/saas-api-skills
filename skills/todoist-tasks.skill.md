---
name: todoist-tasks
description: Manage Todoist tasks, projects, and labels. Use when the user mentions
  todoist, task, project, label.
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
- create_close: Close a task (POST /rest/v2/tasks/{taskId}/close)
- list_projects: List projects (GET /rest/v2/projects)
- create_projects: Create a project (POST /rest/v2/projects)
- list_labels: List labels (GET /rest/v2/labels)
- list_sections: List sections (GET /rest/v2/sections)

## Fields

- `content`: string [REQUIRED for create]
- `project_id`: string [OPTIONAL]
- `section_id`: string [OPTIONAL]
- `description`: string [OPTIONAL]
- `priority`: integer [OPTIONAL] (1-4, 4 is highest)
- `due_string`: string [OPTIONAL] (e.g., "tomorrow", "every monday")
- `labels`: array of strings [OPTIONAL]

## Example Request Bodies

**Create Task:**
```json
{"content": "Review pull request #42", "description": "Check for security issues", "priority": 4, "due_string": "tomorrow", "labels": ["work", "urgent"]}
```

**Create Project:**
```json
{"name": "Q2 Sprint"}
```
