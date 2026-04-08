---
name: jenkins-jobs
description: Manage Jenkins jobs, builds, and nodes. Use when the user mentions jenkins,
  job, build, pipeline, CI/CD, node.
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
- list_json: Get job details (GET /job/{jobName}/api/json)
- create: Trigger a build (POST /job/{jobName}/build)
- create_buildwithparameters: Trigger a parameterized build (POST /job/{jobName}/buildWithParameters)
- list_json_2: Get build details (GET /job/{jobName}/{buildNumber}/api/json)
- create_stop: Stop a build (POST /job/{jobName}/{buildNumber}/stop)
- list_json_3: Get last build (GET /job/{jobName}/lastBuild/api/json)
- list_json_4: List nodes (GET /computer/api/json)
- list_json_5: Get build queue (GET /queue/api/json)
- create_createitem: Create a job (POST /createItem)

## Fields

- `name`: string [REQUIRED for create] (job name as query parameter)
- `mode`: string [REQUIRED for create] (e.g., "hudson.model.FreeStyleProject")
- `parameters`: object [OPTIONAL for parameterized build]

## Example Request Bodies

**Create Job:**
```json
{"name": "my-pipeline", "mode": "hudson.model.FreeStyleProject"}
```

**Trigger Parameterized Build:**
```json
{"parameters": {"BRANCH": "main", "DEPLOY_ENV": "staging"}}
```
