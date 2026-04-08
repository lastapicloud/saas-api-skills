---
name: penpot-design
description: Manage projects and files via Penpot. Use when the user mentions penpot,
  design, project, file, prototype, open source design.
version: 1.0.0
skill_type: external
base_url_env: PENPOT_BASE_URL
auth_env_var: PENPOT_ACCESS_TOKEN
auth_type: bearer
triggers:
  - penpot
  - design
  - project
  - file
  - prototype
  - open source design
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires PENPOT_BASE_URL and PENPOT_ACCESS_TOKEN environment variables.
---

# Penpot-Design

Manage projects and files via Penpot. Use when the user mentions penpot, design, project, file, prototype, open source design.

## API Endpoints

- **GET** `/api/rpc/command/get-projects` - List projects
- **POST** `/api/rpc/command/create-project` - Create project
- **GET** `/api/rpc/command/get-project` - Get project
- **GET** `/api/rpc/command/get-project-files` - List project files
- **POST** `/api/rpc/command/create-file` - Create file
- **GET** `/api/rpc/command/get-file` - Get file
- **DELETE** `/api/rpc/command/delete-project` - Delete project
- **GET** `/api/rpc/command/get-teams` - List teams

## Actions

- list: List projects (GET /api/rpc/command/get-projects)
- create: Create project (POST /api/rpc/command/create-project)
- list_get_project: Get project (GET /api/rpc/command/get-project)
- list_get_project_files: List project files (GET /api/rpc/command/get-project-files)
- create_create_file: Create file (POST /api/rpc/command/create-file)
- list_get_file: Get file (GET /api/rpc/command/get-file)
- delete_delete_project: Delete project (DELETE /api/rpc/command/delete-project)
- list_get_teams: List teams (GET /api/rpc/command/get-teams)

## Fields

- `name`: string [REQUIRED for create]
- `team-id`: string [REQUIRED for create]
- `project-id`: string [REQUIRED for create_file]

## Example Request Bodies

**Create Project:**
```json
{"name": "Mobile App Redesign", "team-id": "team-abc123"}
```

**Create File:**
```json
{"name": "Login Screen Mockup", "project-id": "proj-xyz789"}
```
