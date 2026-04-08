---
name: gitlab-repos
description: Manage GitLab projects, issues, merge requests, and pipelines. Use when
  the user mentions gitlab, project, merge request, MR, pipeline, CI/CD, issue, repository.
version: 1.0.0
skill_type: external
base_url_env: GITLAB_BASE_URL
auth_env_var: GITLAB_API_TOKEN
auth_type: header
triggers:
  - gitlab
  - project
  - merge request
  - MR
  - pipeline
  - CI/CD
  - issue
  - repository
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires GITLAB_BASE_URL and GITLAB_API_TOKEN environment variables.
---

# Gitlab-Repos

Manage GitLab projects, issues, merge requests, and pipelines. Use when the user mentions gitlab, project, merge request, MR, pipeline, CI/CD, issue, repository.

## API Endpoints

- **GET** `/projects` - List projects
- **GET** `/projects/{id}` - Get a project
- **POST** `/projects/{id}/issues` - Create an issue
- **GET** `/projects/{id}/issues` - List project issues
- **POST** `/projects/{id}/merge_requests` - Create a merge request
- **GET** `/projects/{id}/merge_requests` - List merge requests
- **GET** `/projects/{id}/pipelines` - List pipelines
- **POST** `/projects/{id}/pipeline` - Trigger a pipeline
- **GET** `/projects/:id` - Supported attributes:
- **GET** `/users/:user_id/projects` - Supported attributes:
- **GET** `/users/:user_id/contributed_projects` - Supported attributes:
- **GET** `/projects/:id/users` - Supported attributes:
- **GET** `/projects/:id/groups` - Supported attributes:
- **GET** `/projects/:id/share_locations` - Supported attributes:
- **GET** `/projects/:id/invited_groups` - Supported attributes:

## Actions

- list: List projects (GET /projects)
- get_by_id: Get a project (GET /projects/{id})
- create: Create an issue (POST /projects/{id}/issues)
- list_issues: List project issues (GET /projects/{id}/issues)
- create_merge_requests: Create a merge request (POST /projects/{id}/merge_requests)
- list_merge_requests: List merge requests (GET /projects/{id}/merge_requests)
- list_pipelines: List pipelines (GET /projects/{id}/pipelines)
- create_pipeline: Trigger a pipeline (POST /projects/{id}/pipeline)
- list_id: Supported attributes: (GET /projects/:id)
- list_projects: Supported attributes: (GET /users/:user_id/projects)
- list_contributed_projects: Supported attributes: (GET /users/:user_id/contributed_projects)
- list_users: Supported attributes: (GET /projects/:id/users)
- list_groups: Supported attributes: (GET /projects/:id/groups)
- list_share_locations: Supported attributes: (GET /projects/:id/share_locations)
- list_invited_groups: Supported attributes: (GET /projects/:id/invited_groups)

## Fields

- `id`: string [REQUIRED for project-scoped actions] (project ID or URL-encoded path)
- `title`: string [REQUIRED for create_issue, create_merge_request]
- `description`: string [OPTIONAL] (issue or MR description)
- `source_branch`: string [REQUIRED for create_merge_request] (branch with changes)
- `target_branch`: string [REQUIRED for create_merge_request] (target branch, default: main)
- `labels`: string [OPTIONAL for create_issue] (comma-separated label names)
- `assignee_ids`: array [OPTIONAL for create_issue] (user IDs to assign)
- `state`: string [OPTIONAL] (filter by state: opened, closed, merged, all)
- `ref`: string [REQUIRED for trigger_pipeline] (branch or tag to run pipeline on)

## Example Request Bodies

**Create Issue:**
```json
{"title": "Fix login bug", "description": "The login page returns a 500 error", "labels": "bug,urgent"}
```

**Create Merge Request:**
```json
{"title": "Fix login bug", "description": "Resolves #42", "source_branch": "fix-login", "target_branch": "main"}
```

**Trigger Pipeline:**
```json
{"ref": "main"}
```
