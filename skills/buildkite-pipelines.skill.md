---
name: buildkite-pipelines
description: Manage Buildkite pipelines, builds, and agents. Use when the user mentions
  buildkite, pipeline, build, agent, CI/CD.
version: 1.0.0
skill_type: external
base_url_env: BUILDKITE_BASE_URL
auth_env_var: BUILDKITE_API_TOKEN
auth_type: bearer
triggers:
  - buildkite
  - pipeline
  - build
  - agent
  - CI/CD
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires BUILDKITE_BASE_URL and BUILDKITE_API_TOKEN environment variables.
---

# Buildkite-Pipelines

Manage Buildkite pipelines, builds, and agents. Use when the user mentions buildkite, pipeline, build, agent, CI/CD.

## API Endpoints

- **GET** `/v2/organizations/{org}/pipelines` - List pipelines
- **GET** `/v2/organizations/{org}/pipelines/{pipeline}` - Get a pipeline
- **POST** `/v2/organizations/{org}/pipelines` - Create a pipeline
- **DELETE** `/v2/organizations/{org}/pipelines/{pipeline}` - Delete a pipeline
- **GET** `/v2/organizations/{org}/pipelines/{pipeline}/builds` - List builds
- **POST** `/v2/organizations/{org}/pipelines/{pipeline}/builds` - Create a build
- **GET** `/v2/organizations/{org}/pipelines/{pipeline}/builds/{number}` - Get a build
- **PUT** `/v2/organizations/{org}/pipelines/{pipeline}/builds/{number}/cancel` - Cancel a build
- **GET** `/v2/organizations/{org}/agents` - List agents
- **GET** `/v2/organizations` - List organizations

## Actions

- list: List pipelines (GET /v2/organizations/{org}/pipelines)
- get_by_id: Get a pipeline (GET /v2/organizations/{org}/pipelines/{pipeline})
- create: Create a pipeline (POST /v2/organizations/{org}/pipelines)
- delete: Delete a pipeline (DELETE /v2/organizations/{org}/pipelines/{pipeline})
- list_builds: List builds (GET /v2/organizations/{org}/pipelines/{pipeline}/builds)
- create_builds: Create a build (POST /v2/organizations/{org}/pipelines/{pipeline}/builds)
- get_by_id_builds: Get a build (GET /v2/organizations/{org}/pipelines/{pipeline}/builds/{number})
- put_cancel: Cancel a build (PUT /v2/organizations/{org}/pipelines/{pipeline}/builds/{number}/cancel)
- list_agents: List agents (GET /v2/organizations/{org}/agents)
- list_organizations: List organizations (GET /v2/organizations)

## Fields

- `name`: string [REQUIRED for create pipeline]
- `repository`: string [REQUIRED for create pipeline]
- `commit`: string [REQUIRED for create build] (e.g., "HEAD")
- `branch`: string [REQUIRED for create build]
- `message`: string [OPTIONAL]
- `env`: object [OPTIONAL]

## Example Request Bodies

**Create Pipeline:**
```json
{"name": "Deploy Pipeline", "repository": "git@github.com:org/repo.git"}
```

**Create Build:**
```json
{"commit": "HEAD", "branch": "main", "message": "Deploy to production"}
