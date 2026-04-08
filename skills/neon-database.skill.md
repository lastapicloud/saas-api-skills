---
name: neon-database
description: Manage serverless Postgres databases via Neon. Use when the user mentions
  neon, serverless postgres, database, branch, project.
version: 1.0.0
skill_type: external
base_url_env: NEON_BASE_URL
auth_env_var: NEON_API_KEY
auth_type: bearer
triggers:
  - neon
  - serverless postgres
  - database
  - branch
  - project
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires NEON_BASE_URL and NEON_API_KEY environment variables.
---

# Neon-Database

Manage serverless Postgres databases via Neon. Use when the user mentions neon, serverless postgres, database, branch, project.

## API Endpoints

- **GET** `/projects` - List projects
- **POST** `/projects` - Create project
- **GET** `/projects/{project_id}` - Get project
- **DELETE** `/projects/{project_id}` - Delete project
- **GET** `/projects/{project_id}/branches` - List branches
- **POST** `/projects/{project_id}/branches` - Create branch
- **GET** `/projects/{project_id}/endpoints` - List endpoints
- **GET** `/projects/{project_id}/databases` - List databases

## Actions

- list: List projects (GET /projects)
- create: Create project (POST /projects)
- get_by_id: Get project (GET /projects/{project_id})
- delete: Delete project (DELETE /projects/{project_id})
- list_branches: List branches (GET /projects/{project_id}/branches)
- create_branches: Create branch (POST /projects/{project_id}/branches)
- list_endpoints: List endpoints (GET /projects/{project_id}/endpoints)
- list_databases: List databases (GET /projects/{project_id}/databases)

## Fields

- `project`: object [REQUIRED for create]
- `name`: string [OPTIONAL]

## Example Request Bodies

**Create Project:**
```json
{"project": {"name": "my-app-db"}}
```

**Create Branch:**
```json
{"branch": {"name": "feature/auth-module"}, "parent_branch": "main"}
```
