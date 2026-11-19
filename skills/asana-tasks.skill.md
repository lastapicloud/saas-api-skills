---
name: asana-tasks
description: 'Create, search, and manage Asana tasks, projects, and workspaces. Use
  when the user mentions asana, asana task, asana project, workspace.

  '
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
annotations:
  readOnlyHint: false
  destructiveHint: true
  idempotentHint: false
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
- list_projects_workspace: List projects in a workspace (GET /projects)
- list_workspaces: List all workspaces (GET /workspaces)
- get_multiple_allocations: Get multiple allocations (GET /allocations)
- create_allocation: Create an allocation (POST /allocations)
- update_allocation: Update an allocation (PUT /allocations/{allocation_gid})
- delete_allocation: Delete an allocation (DELETE /allocations/{allocation_gid})
- get_budgets: Get all budgets (GET /budgets)
- create_budget: Create a budget (POST /budgets)
- update_budget: Update a budget (PUT /budgets/{budget_gid})
- delete_budget: Delete a budget (DELETE /budgets/{budget_gid})

## Fields

- `workspace`: string (workspace GID) [REQUIRED for create] — Workspace
- `projects`: array of strings (project GIDs) [OPTIONAL] — List of projects
- `name`: string [REQUIRED for create] — Display name
- `notes`: string [OPTIONAL] (task description/body) — Notes
- `assignee`: string (user GID or email) [OPTIONAL] — Assigned user or agent
- `due_on`: string (YYYY-MM-DD) [OPTIONAL] — Due On
- `completed`: boolean [OPTIONAL] — Whether completed is enabled

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
