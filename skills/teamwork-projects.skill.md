---
name: teamwork-projects
description: Manage Teamwork projects, tasks, and milestones. Use when the user mentions
  teamwork, project, task, milestone.
version: 1.0.0
skill_type: external
base_url_env: TEAMWORK_BASE_URL
auth_env_var: TEAMWORK_API_TOKEN
auth_type: bearer
triggers:
  - teamwork
  - project
  - task
  - milestone
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires TEAMWORK_BASE_URL and TEAMWORK_API_TOKEN environment variables.
---

# Teamwork-Projects

Manage Teamwork projects, tasks, and milestones. Use when the user mentions teamwork, project, task, milestone.

## API Endpoints

- **GET** `/projects.json` - List projects
- **GET** `/projects/{projectId}.json` - Get a project
- **POST** `/projects.json` - Create a project
- **PUT** `/projects/{projectId}.json` - Update a project
- **DELETE** `/projects/{projectId}.json` - Delete a project
- **GET** `/projects/{projectId}/tasks.json` - List tasks in a project
- **POST** `/projects/{projectId}/tasks.json` - Create a task
- **PUT** `/tasks/{taskId}.json` - Update a task
- **GET** `/milestones.json` - List milestones
- **GET** `/people.json` - List people

## Actions

- list: List projects (GET /projects.json)
- list_projects: Get a project (GET /projects/{projectId}.json)
- create: Create a project (POST /projects.json)
- update_projects: Update a project (PUT /projects/{projectId}.json)
- delete_projects: Delete a project (DELETE /projects/{projectId}.json)
- list_tasks_json: List tasks in a project (GET /projects/{projectId}/tasks.json)
- create_tasks_json: Create a task (POST /projects/{projectId}/tasks.json)
- update_tasks: Update a task (PUT /tasks/{taskId}.json)
- list_milestones_json: List milestones (GET /milestones.json)
- list_people_json: List people (GET /people.json)

## Fields

- `name`: string [REQUIRED for create]
- `description`: string [OPTIONAL]
- `content`: string [REQUIRED for create task]
- `start-date`: string [OPTIONAL]
- `due-date`: string [OPTIONAL]
- `responsible-party-id`: string [OPTIONAL]
- `priority`: string [OPTIONAL]

## Example Request Bodies

**Create Project:**
```json
{"name": "Website Redesign", "description": "Complete overhaul of the marketing site"}
```

**Create Task:**
```json
{"content": "Design new homepage mockup", "due-date": "2026-04-15", "priority": "high"}
```
