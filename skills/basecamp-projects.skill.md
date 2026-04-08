---
name: basecamp-projects
description: Manage projects, to-dos, and messages via Basecamp. Use when the user
  mentions basecamp, project, todo, message, campfire, hill chart.
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
- get_by_id: Get project details (GET /projects/{projectId}.json)
- update: Update a project (PATCH /projects/{projectId}.json)
- delete: Delete a project (DELETE /projects/{projectId}.json)
- list_todolists: List to-do lists (GET /buckets/{projectId}/todolists.json)
- create_todolists: Create a to-do list (POST /buckets/{projectId}/todolists.json)
- update_todolists: Update a to-do list (PATCH /buckets/{projectId}/todolists/{todolistId}.json)
- delete_todolists: Delete a to-do list (DELETE /buckets/{projectId}/todolists/{todolistId}.json)
- list_todos: List to-dos (GET /buckets/{projectId}/todolists/{todolistId}/todos.json)
- create_todos: Create a to-do (POST /buckets/{projectId}/todolists/{todolistId}/todos.json)
- update_todos: Update a to-do (PATCH /buckets/{projectId}/todos/{todoId}.json)
- delete_todos: Delete a to-do (DELETE /buckets/{projectId}/todos/{todoId}.json)
- list_messages: List messages (GET /buckets/{projectId}/message_boards/{boardId}/messages.json)
- create_messages: Create a message (POST /buckets/{projectId}/message_boards/{boardId}/messages.json)

## Fields

- `name`: string [REQUIRED for create]
- `description`: string [OPTIONAL]
- `content`: string [REQUIRED for create_todo]

## Example Request Bodies

**Create Project:**
```json
{"name": "Website Redesign", "description": "Redesign the company website for 2025"}
```

**Create To-Do:**
```json
{"content": "Review homepage mockup", "description": "Check the new design against brand guidelines"}
