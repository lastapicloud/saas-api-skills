---
name: octopusdeploy-deployments
description: 'Manage Octopus Deploy projects, releases, and deployments. Use when
  the user mentions octopus, octopus deploy, deployment, release, environment.

  '
version: 1.0.0
skill_type: external
base_url_env: OCTOPUSDEPLOY_BASE_URL
auth_env_var: OCTOPUSDEPLOY_API_KEY
auth_type: header
triggers:
  - octopus
  - octopus deploy
  - deployment
  - release
  - environment
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires OCTOPUSDEPLOY_BASE_URL and OCTOPUSDEPLOY_API_KEY environment
  variables.
annotations:
  readOnlyHint: false
  destructiveHint: false
  idempotentHint: false
---

# Octopusdeploy-Deployments

Manage Octopus Deploy projects, releases, and deployments. Use when the user mentions octopus, octopus deploy, deployment, release, environment.


## API Endpoints

- **GET** `/api/projects` - List projects
- **GET** `/api/projects/{projectId}` - Get a project
- **POST** `/api/projects` - Create a project
- **GET** `/api/releases` - List releases
- **POST** `/api/releases` - Create a release
- **GET** `/api/deployments` - List deployments
- **POST** `/api/deployments` - Create a deployment
- **GET** `/api/environments` - List environments
- **GET** `/api/tenants` - List tenants
- **GET** `/api/spaces` - List spaces

## Actions

- list: List projects (GET /api/projects)
- get_by_id: Get a project (GET /api/projects/{projectId})
- create: Create a project (POST /api/projects)
- list_releases: List releases (GET /api/releases)
- create_release: Create a release (POST /api/releases)
- list_deployments: List deployments (GET /api/deployments)
- create_deployment: Create a deployment (POST /api/deployments)
- list_environments: List environments (GET /api/environments)
- list_tenants: List tenants (GET /api/tenants)
- list_spaces: List spaces (GET /api/spaces)

## Fields

- `Name`: string [REQUIRED for create project] — Display name
- `ProjectGroupId`: string [REQUIRED for create project] — Projectgroup unique identifier
- `LifecycleId`: string [REQUIRED for create project] — Lifecycle unique identifier
- `ProjectId`: string [REQUIRED for create release] — Project unique identifier
- `Version`: string [REQUIRED for create release] — Version
- `ReleaseId`: string [REQUIRED for create deployment] — Release unique identifier
- `EnvironmentId`: string [REQUIRED for create deployment] — Environment unique identifier

## Example Request Bodies

**Create Project:**
```json
{"Name": "Web API Service", "ProjectGroupId": "ProjectGroups-1", "LifecycleId": "Lifecycles-1"}
```

**Create Deployment:**
```json
{"ReleaseId": "Releases-42", "EnvironmentId": "Environments-1"}
```

## Response

**Project object:**
- `id`: string — Unique project identifier
- `name`: string — Project name or title
- `status`: string — Current status
- `created_at`: string — Creation timestamp (ISO 8601)
- `updated_at`: string — Last update timestamp (ISO 8601)


**Required fields reference:**
```json
{
  "ProjectId": "example_ProjectId",
  "Version": "example_Version"
}
```


**Required fields reference:**
```json
{
  "ProjectId": "example_ProjectId",
  "Version": "example_Version"
}
```

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
