---
name: azuredevops-repos
description: 'Manage Azure DevOps repositories, work items, and pipelines. Use when
  the user mentions azure devops, ADO, work item, repository, pipeline, board.

  '
version: 1.0.0
skill_type: external
base_url_env: AZURE_DEVOPS_BASE_URL
auth_env_var: AZURE_DEVOPS_PAT
auth_type: basic
triggers:
  - azure devops
  - ADO
  - work item
  - repository
  - pipeline
  - board
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires AZURE_DEVOPS_BASE_URL and AZURE_DEVOPS_PAT environment variables.
annotations:
  readOnlyHint: false
  destructiveHint: true
  idempotentHint: false
---

# Azuredevops-Repos

Manage Azure DevOps repositories, work items, and pipelines. Use when the user mentions azure devops, ADO, work item, repository, pipeline, board.


## API Endpoints

- **GET** `/{organization}/{project}/_apis/git/repositories` - List repositories
- **GET** `/{organization}/{project}/_apis/git/repositories/{repositoryId}` - Get a repository
- **GET** `/{organization}/{project}/_apis/wit/workitems/{id}` - Get a work item
- **POST** `/{organization}/{project}/_apis/wit/workitems/$Task` - Create a work item
- **PATCH** `/{organization}/{project}/_apis/wit/workitems/{id}` - Update a work item
- **DELETE** `/{organization}/{project}/_apis/wit/workitems/{id}` - Delete a work item
- **GET** `/{organization}/{project}/_apis/pipelines` - List pipelines
- **POST** `/{organization}/{project}/_apis/pipelines/{pipelineId}/runs` - Run a pipeline
- **GET** `/{organization}/{project}/_apis/git/repositories/{repositoryId}/pullrequests` - List PRs
- **POST** `/{organization}/{project}/_apis/git/repositories/{repositoryId}/pullrequests` - Create a PR

## Actions

- list: List repositories (GET /{organization}/{project}/_apis/git/repositories)
- get_by_id: Get a repository (GET /{organization}/{project}/_apis/git/repositories/{repositoryId})
- get_work_item: Get a work item (GET /{organization}/{project}/_apis/wit/workitems/{id})
- create: Create a work item (POST /{organization}/{project}/_apis/wit/workitems/$Task)
- update: Update a work item (PATCH /{organization}/{project}/_apis/wit/workitems/{id})
- delete: Delete a work item (DELETE /{organization}/{project}/_apis/wit/workitems/{id})
- list_pipelines: List pipelines (GET /{organization}/{project}/_apis/pipelines)
- create_run_pipeline: Run a pipeline (POST /{organization}/{project}/_apis/pipelines/{pipelineId}/runs)
- list_prs: List PRs (GET /{organization}/{project}/_apis/git/repositories/{repositoryId}/pullrequests)
- create_pr: Create a PR (POST /{organization}/{project}/_apis/git/repositories/{repositoryId}/pullrequests)

## Fields

- `op`: string [REQUIRED for create/update work item] ("add") — Op
- `path`: string [REQUIRED] (e.g., "/fields/System.Title") — Path
- `value`: string [REQUIRED] — Value
- `sourceRefName`: string [REQUIRED for create PR] — Sourceref display name
- `targetRefName`: string [REQUIRED for create PR] — Targetref display name
- `title`: string [REQUIRED for create PR] — Title or heading

## Example Request Bodies

**Create Work Item:**
```json
[{"op": "add", "path": "/fields/System.Title", "value": "Fix login timeout issue"}]
```

**Create Pull Request:**
```json
{"sourceRefName": "refs/heads/feature/login-fix", "targetRefName": "refs/heads/main", "title": "Fix login timeout issue"}
```

## Response

**Workitem object:**
- `id`: string — Unique workitem identifier
- `name`: string — Workitem name or title
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
