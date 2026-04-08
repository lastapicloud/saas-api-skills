---
name: asana-tasks
description: Create, search, and manage Asana tasks, projects, and workspaces. Use
  when the user mentions asana, asana task, asana project, workspace.
version: 1.0.0
skill_type: external
base_url_env: ASANA_BASE_URL
auth_env_var: ASANA_API_TOKEN
auth_type: bearer
triggers:
  - asana
  - asana task
  - asana project
  - workspace
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires ASANA_BASE_URL and ASANA_API_TOKEN environment variables.
---

# Asana-Tasks

Create, search, and manage Asana tasks, projects, and workspaces. Use when the user mentions asana, asana task, asana project, workspace.

## API Endpoints

- **GET** `/tasks` - List tasks (requires project or assignee filter)
- **GET** `/tasks/{task_gid}` - Get a specific task
- **POST** `/tasks` - Create a new task
- **PUT** `/tasks/{task_gid}` - Update a task
- **DELETE** `/tasks/{task_gid}` - Delete a task
- **GET** `/projects` - List projects in a workspace
- **GET** `/workspaces` - List all workspaces
- **GET** `/allocations` - Get multiple allocations
- **POST** `/allocations` - Create an allocation
- **PUT** `/allocations/{allocation_gid}` - Update an allocation
- **DELETE** `/allocations/{allocation_gid}` - Delete an allocation
- **GET** `/budgets` - Get all budgets
- **POST** `/budgets` - Create a budget
- **PUT** `/budgets/{budget_gid}` - Update a budget
- **DELETE** `/budgets/{budget_gid}` - Delete a budget

## Actions

- list: List tasks (requires project or assignee filter) (GET /tasks)
- get_by_id: Get a specific task (GET /tasks/{task_gid})
- create: Create a new task (POST /tasks)
- update: Update a task (PUT /tasks/{task_gid})
- delete: Delete a task (DELETE /tasks/{task_gid})
- list_projects: List projects in a workspace (GET /projects)
- list_workspaces: List all workspaces (GET /workspaces)
- list_allocations: Get multiple allocations (GET /allocations)
- create_allocations: Create an allocation (POST /allocations)
- update_allocations: Update an allocation (PUT /allocations/{allocation_gid})
- delete_allocations: Delete an allocation (DELETE /allocations/{allocation_gid})
- list_budgets: Get all budgets (GET /budgets)
- create_budgets: Create a budget (POST /budgets)
- update_budgets: Update a budget (PUT /budgets/{budget_gid})
- delete_budgets: Delete a budget (DELETE /budgets/{budget_gid})

## Fields

- `workspace`: string (workspace GID) [REQUIRED for create]
- `projects`: array of strings (project GIDs) [OPTIONAL]
- `name`: string [REQUIRED for create]
- `notes`: string [OPTIONAL] (task description/body)
- `assignee`: string (user GID or email) [OPTIONAL]
- `due_on`: string (YYYY-MM-DD) [OPTIONAL]
- `completed`: boolean [OPTIONAL]

## Example Request Bodies

**Create Task:**
```json
{"data": {"workspace": "12345", "name": "Fix login bug", "projects": ["67890"], "notes": "The login page returns a 500 error", "due_on": "2026-04-01"}}
```

**Update Task:**
```json
{"data": {"name": "Fix login bug (urgent)", "completed": false}}
```

**List Tasks (Query Params):**
Query parameter: `project=67890&opt_fields=name,completed,due_on,assignee`
