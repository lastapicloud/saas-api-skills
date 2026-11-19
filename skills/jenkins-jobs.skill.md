---
name: jenkins-jobs
description: 'Manage Jenkins jobs, builds, and nodes. Use when the user mentions jenkins,
  job, build, pipeline, CI/CD, node.

  '
version: 1.0.0
skill_type: external
base_url_env: JENKINS_BASE_URL
auth_env_var: JENKINS_API_TOKEN
auth_user_env: JENKINS_USERNAME
auth_type: basic
triggers:
  - jenkins
  - job
  - build
  - pipeline
  - CI/CD
  - node
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires JENKINS_BASE_URL and JENKINS_API_TOKEN environment variables.
annotations:
  readOnlyHint: false
  destructiveHint: false
  idempotentHint: false
---

# Jenkins-Jobs

Manage Jenkins jobs, builds, and nodes. Use when the user mentions jenkins, job, build, pipeline, CI/CD, node.


## API Endpoints

- **GET** `/api/json` - List jobs (top-level)
- **GET** `/job/{jobName}/api/json` - Get job details
- **POST** `/job/{jobName}/build` - Trigger a build
- **POST** `/job/{jobName}/buildWithParameters` - Trigger a parameterized build
- **GET** `/job/{jobName}/{buildNumber}/api/json` - Get build details
- **POST** `/job/{jobName}/{buildNumber}/stop` - Stop a build
- **GET** `/job/{jobName}/lastBuild/api/json` - Get last build
- **GET** `/computer/api/json` - List nodes
- **GET** `/queue/api/json` - Get build queue
- **POST** `/createItem` - Create a job

## Actions

- list: List jobs (top-level) (GET /api/json)
- get_job_details: Get job details (GET /job/{jobName}/api/json)
- create: Trigger a build (POST /job/{jobName}/build)
- trigger_parameterized_build: Trigger a parameterized build (POST /job/{jobName}/buildWithParameters)
- get_build_details: Get build details (GET /job/{jobName}/{buildNumber}/api/json)
- stop_build: Stop a build (POST /job/{jobName}/{buildNumber}/stop)
- get_last_build: Get last build (GET /job/{jobName}/lastBuild/api/json)
- list_nodes: List nodes (GET /computer/api/json)
- get_build_queue: Get build queue (GET /queue/api/json)
- create_job: Create a job (POST /createItem)

## Fields

- `name`: string [REQUIRED for create] (job name as query parameter) — Display name
- `mode`: string [REQUIRED for create] (e.g., "hudson.model.FreeStyleProject") — Mode
- `parameters`: object [OPTIONAL for parameterized build] — Parameters configuration

## Example Request Bodies

**Create Job:**
```json
{"name": "my-pipeline", "mode": "hudson.model.FreeStyleProject"}
```

**Trigger Parameterized Build:**
```json
{"parameters": {"BRANCH": "main", "DEPLOY_ENV": "staging"}}
```

## Response

**Json object:**
- `id`: string — Unique json identifier
- `name`: string — Json name or title
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
