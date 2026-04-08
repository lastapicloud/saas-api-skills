---
name: azuredevops-repos
description: Manage Azure DevOps repositories, work items, and pipelines. Use when
  the user mentions azure devops, ADO, work item, repository, pipeline, board.
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
- get_by_id_workitems: Get a work item (GET /{organization}/{project}/_apis/wit/workitems/{id})
- create: Create a work item (POST /{organization}/{project}/_apis/wit/workitems/$Task)
- update: Update a work item (PATCH /{organization}/{project}/_apis/wit/workitems/{id})
- delete: Delete a work item (DELETE /{organization}/{project}/_apis/wit/workitems/{id})
- list_pipelines: List pipelines (GET /{organization}/{project}/_apis/pipelines)
- create_runs: Run a pipeline (POST /{organization}/{project}/_apis/pipelines/{pipelineId}/runs)
- list_pullrequests: List PRs (GET /{organization}/{project}/_apis/git/repositories/{repositoryId}/pullrequests)
- create_pullrequests: Create a PR (POST /{organization}/{project}/_apis/git/repositories/{repositoryId}/pullrequests)

## Fields

- `op`: string [REQUIRED for create/update work item] ("add")
- `path`: string [REQUIRED] (e.g., "/fields/System.Title")
- `value`: string [REQUIRED]
- `sourceRefName`: string [REQUIRED for create PR]
- `targetRefName`: string [REQUIRED for create PR]
- `title`: string [REQUIRED for create PR]

## Example Request Bodies

**Create Work Item:**
```json
[{"op": "add", "path": "/fields/System.Title", "value": "Fix login timeout issue"}]
```

**Create Pull Request:**
```json
{"sourceRefName": "refs/heads/feature/login-fix", "targetRefName": "refs/heads/main", "title": "Fix login timeout issue"}
```
