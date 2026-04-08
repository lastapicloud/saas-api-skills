---
name: clickup-tasks
description: Create, search, and manage ClickUp tasks, lists, and spaces. Use when
  the user mentions clickup, click up.
version: 1.0.0
skill_type: external
base_url_env: CLICKUP_BASE_URL
auth_env_var: CLICKUP_API_TOKEN
auth_type: bearer
triggers:
  - clickup
  - click up
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires CLICKUP_BASE_URL and CLICKUP_API_TOKEN environment variables.
---

# Clickup-Tasks

Create, search, and manage ClickUp tasks, lists, and spaces. Use when the user mentions clickup, click up.

## API Endpoints

- **GET** `/list/{list_id}/task` - List tasks in a list
- **GET** `/task/{task_id}` - Get a specific task
- **POST** `/list/{list_id}/task` - Create a new task in a list
- **PUT** `/task/{task_id}` - Update a task
- **DELETE** `/task/{task_id}` - Delete a task
- **GET** `/team/{team_id}/space` - List spaces in a workspace
- **GET** `/space/{space_id}/list` - List lists in a space
- **GET** `/questions` - List All Questions
- **POST** `/questions` - Create a New Question

## Actions

- list: List tasks in a list (GET /list/{list_id}/task)
- get_by_id: Get a specific task (GET /task/{task_id})
- create: Create a new task in a list (POST /list/{list_id}/task)
- update: Update a task (PUT /task/{task_id})
- delete: Delete a task (DELETE /task/{task_id})
- list_space: List spaces in a workspace (GET /team/{team_id}/space)
- list_space_2: List lists in a space (GET /space/{space_id}/list)
- list_questions: List All Questions (GET /questions)
- create_questions: Create a New Question (POST /questions)

## Fields

- `name`: string [REQUIRED for create]
- `description`: string [OPTIONAL]
- `assignees`: array of integers (user IDs) [OPTIONAL]
- `status`: string [OPTIONAL] (e.g., "Open", "In Progress", "Closed")
- `priority`: integer [OPTIONAL] (1=Urgent, 2=High, 3=Normal, 4=Low)
- `due_date`: integer (Unix timestamp in ms) [OPTIONAL]
- `tags`: array of strings [OPTIONAL]

## Example Request Bodies

**Create Task:**
```json
{"name": "Fix login bug", "description": "The login page returns a 500 error", "priority": 2, "status": "Open"}
```

**Update Task:**
```json
{"name": "Fix login bug (urgent)", "priority": 1, "status": "In Progress"}
```
