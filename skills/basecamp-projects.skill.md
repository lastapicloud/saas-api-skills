---
name: basecamp-projects
description: 'Manage projects, to-dos, and messages via Basecamp. Use when the user
  mentions basecamp, project, todo, message, campfire, hill chart.

  '
version: 1.0.0
skill_type: external
base_url_env: BASECAMP_BASE_URL
auth_env_var: BASECAMP_ACCESS_TOKEN
auth_type: bearer
triggers:
  - basecamp
  - project
  - todo
  - message
  - campfire
  - hill chart
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires BASECAMP_BASE_URL and BASECAMP_ACCESS_TOKEN environment variables.
annotations:
  readOnlyHint: false
  destructiveHint: true
  idempotentHint: false
---

# Basecamp-Projects

Manage projects, to-dos, and messages via Basecamp. Use when the user mentions basecamp, project, todo, message, campfire, hill chart.


## API Endpoints

- **GET** `/projects.json` - List projects
- **POST** `/projects.json` - Create a project
- **GET** `/projects/{projectId}.json` - Get project details
- **PATCH** `/projects/{projectId}.json` - Update a project
- **DELETE** `/projects/{projectId}.json` - Delete a project
- **GET** `/buckets/{projectId}/todolists.json` - List to-do lists
- **POST** `/buckets/{projectId}/todolists.json` - Create a to-do list
- **PATCH** `/buckets/{projectId}/todolists/{todolistId}.json` - Update a to-do list
- **DELETE** `/buckets/{projectId}/todolists/{todolistId}.json` - Delete a to-do list
- **GET** `/buckets/{projectId}/todolists/{todolistId}/todos.json` - List to-dos
- **POST** `/buckets/{projectId}/todolists/{todolistId}/todos.json` - Create a to-do
- **PATCH** `/buckets/{projectId}/todos/{todoId}.json` - Update a to-do
- **DELETE** `/buckets/{projectId}/todos/{todoId}.json` - Delete a to-do
- **GET** `/buckets/{projectId}/message_boards/{boardId}/messages.json` - List messages
- **POST** `/buckets/{projectId}/message_boards/{boardId}/messages.json` - Create a message

## Actions

- list: List projects (GET /projects.json)
- create: Create a project (POST /projects.json)
- get_project_details: Get project details (GET /projects/{projectId}.json)
- patch_projects: Update a project (PATCH /projects/{projectId}.json)
- delete_projects: Delete a project (DELETE /projects/{projectId}.json)
- list_todo_lists: List to-do lists (GET /buckets/{projectId}/todolists.json)
- create_todo_list: Create a to-do list (POST /buckets/{projectId}/todolists.json)
- patch_todolists: Update a to-do list (PATCH /buckets/{projectId}/todolists/{todolistId}.json)
- delete_todolists: Delete a to-do list (DELETE /buckets/{projectId}/todolists/{todolistId}.json)
- list_todos: List to-dos (GET /buckets/{projectId}/todolists/{todolistId}/todos.json)
- create_todo: Create a to-do (POST /buckets/{projectId}/todolists/{todolistId}/todos.json)
- patch_todos: Update a to-do (PATCH /buckets/{projectId}/todos/{todoId}.json)
- delete_todos: Delete a to-do (DELETE /buckets/{projectId}/todos/{todoId}.json)
- list_messages: List messages (GET /buckets/{projectId}/message_boards/{boardId}/messages.json)
- create_message: Create a message (POST /buckets/{projectId}/message_boards/{boardId}/messages.json)

## Fields

- `name`: string [REQUIRED for create] — Display name
- `description`: string [OPTIONAL] — Human-readable description
- `content`: string [REQUIRED for create_todo] — Content body

## Example Request Bodies

**Create Project:**
```json
{"name": "Website Redesign", "description": "Redesign the company website for 2025"}
```

**Create To-Do:**
```json
{"content": "Review homepage mockup", "description": "Check the new design against brand guidelines"}

## Response

**Project object:**
- `id`: string — Unique project identifier
- `name`: string — Project name or title
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
