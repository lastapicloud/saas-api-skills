---
name: octopus-deploy
description: Manage projects, releases, and deployments via Octopus Deploy. Use when
  the user mentions octopus deploy, octopus, deployment, release, project, environment.
version: 1.0.0
skill_type: external
base_url_env: OCTOPUS_DEPLOY_BASE_URL
auth_env_var: OCTOPUS_DEPLOY_API_KEY
auth_type: header
triggers:
  - octopus deploy
  - octopus
  - deployment
  - release
  - project
  - environment
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires OCTOPUS_DEPLOY_BASE_URL and OCTOPUS_DEPLOY_API_KEY environment
  variables.
---

# Octopus-Deploy

Manage projects, releases, and deployments via Octopus Deploy. Use when the user mentions octopus deploy, octopus, deployment, release, project, environment.

## API Endpoints

- **GET** `/api/projects` - List projects
- **GET** `/api/projects/{id}` - Get project
- **GET** `/api/releases` - List releases
- **POST** `/api/releases` - Create release
- **GET** `/api/deployments` - List deployments
- **POST** `/api/deployments` - Create deployment
- **GET** `/api/environments` - List environments
- **GET** `/api/machines` - List machines

## Actions

- list: List projects (GET /api/projects)
- get_by_id: Get project (GET /api/projects/{id})
- list_releases: List releases (GET /api/releases)
- create: Create release (POST /api/releases)
- list_deployments: List deployments (GET /api/deployments)
- create_deployments: Create deployment (POST /api/deployments)
- list_environments: List environments (GET /api/environments)
- list_machines: List machines (GET /api/machines)

## Fields

- `ProjectId`: string [REQUIRED for create_release]
- `Version`: string [REQUIRED for create_release]
- `EnvironmentId`: string [REQUIRED for create_deployment]
- `ReleaseId`: string [REQUIRED for create_deployment]

## Example Request Bodies

**Create Release:**
```json
{"ProjectId": "Projects-123", "Version": "1.2.0"}
```

**Create Deployment:**
```json
{"EnvironmentId": "Environments-456", "ReleaseId": "Releases-789"}
```
