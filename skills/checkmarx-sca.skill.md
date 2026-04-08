---
name: checkmarx-sca
description: Manage security scans, projects, and view scan results via the Checkmarx
  One API. Use when the user mentions checkmarx, SAST, DAST, checkmarx scan, checkmarx
  project, application security testing, CxOne.
version: 1.0.0
skill_type: external
base_url_env: CHECKMARX_BASE_URL
auth_env_var: CHECKMARX_API_KEY
auth_type: bearer
triggers:
  - checkmarx
  - SAST
  - DAST
  - checkmarx scan
  - checkmarx project
  - application security testing
  - CxOne
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires CHECKMARX_BASE_URL and CHECKMARX_API_KEY environment variables.
---

# Checkmarx-Sca

Manage security scans, projects, and view scan results via the Checkmarx One API. Use when the user mentions checkmarx, SAST, DAST, checkmarx scan, checkmarx project, application security testing, CxOne.

## API Endpoints

- **GET** `/api/projects` - List all projects
- **POST** `/api/projects` - Create a new project
- **GET** `/api/projects/{id}` - Get project details
- **PUT** `/api/projects/{id}` - Update a project
- **DELETE** `/api/projects/{id}` - Delete a project
- **GET** `/api/scans` - List all scans
- **POST** `/api/scans` - Create a new scan
- **GET** `/api/scans/{id}` - Get scan details
- **GET** `/api/results` - Get scan results
- **GET** `/api/applications` - List all applications

## Actions

- list: List all projects (GET /api/projects)
- create: Create a new project (POST /api/projects)
- get_by_id: Get project details (GET /api/projects/{id})
- update: Update a project (PUT /api/projects/{id})
- delete: Delete a project (DELETE /api/projects/{id})
- list_scans: List all scans (GET /api/scans)
- create_scans: Create a new scan (POST /api/scans)
- get_by_id_scans: Get scan details (GET /api/scans/{id})
- list_results: Get scan results (GET /api/results)
- list_applications: List all applications (GET /api/applications)

## Fields

- `id`: string [REQUIRED for get_project, update_project, delete_project, get_scan] (project or scan ID)
- `name`: string [REQUIRED for create_project] (project name)
- `scan-ids`: string [REQUIRED for get_results] (scan ID to retrieve results for)
- `project-id`: string [REQUIRED for create_scan] (project ID to scan)
- `type`: string [REQUIRED for create_scan] (scan handler: git, upload)
- `repoUrl`: string [OPTIONAL for create_scan] (Git repository URL when type is git)

## Example Request Bodies

**Create Project:**
```json
{"name": "my-project", "groups": ["my-group"]}
```

**Create Scan (Git):**
```json
{"project": {"id": "project-uuid"}, "type": "git", "handler": {"repoUrl": "https://github.com/org/repo", "branch": "main"}}
```
