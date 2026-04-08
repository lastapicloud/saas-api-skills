---
name: octopusdeploy-deployments
description: Manage Octopus Deploy projects, releases, and deployments. Use when the
  user mentions octopus, octopus deploy, deployment, release, environment.
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
- create_releases: Create a release (POST /api/releases)
- list_deployments: List deployments (GET /api/deployments)
- create_deployments: Create a deployment (POST /api/deployments)
- list_environments: List environments (GET /api/environments)
- list_tenants: List tenants (GET /api/tenants)
- list_spaces: List spaces (GET /api/spaces)

## Fields

- `Name`: string [REQUIRED for create project]
- `ProjectGroupId`: string [REQUIRED for create project]
- `LifecycleId`: string [REQUIRED for create project]
- `ProjectId`: string [REQUIRED for create release]
- `Version`: string [REQUIRED for create release]
- `ReleaseId`: string [REQUIRED for create deployment]
- `EnvironmentId`: string [REQUIRED for create deployment]

## Example Request Bodies

**Create Project:**
```json
{"Name": "Web API Service", "ProjectGroupId": "ProjectGroups-1", "LifecycleId": "Lifecycles-1"}
```

**Create Deployment:**
```json
{"ReleaseId": "Releases-42", "EnvironmentId": "Environments-1"}
```
