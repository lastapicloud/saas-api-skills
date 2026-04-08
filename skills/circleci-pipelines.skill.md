---
name: circleci-pipelines
description: Manage pipelines, workflows, and jobs via CircleCI. Use when the user
  mentions circleci, ci, cd, pipeline, workflow, build, continuous integration.
version: 1.0.0
skill_type: external
base_url_env: CIRCLECI_BASE_URL
auth_env_var: CIRCLECI_API_TOKEN
auth_type: header
triggers:
  - circleci
  - ci
  - cd
  - pipeline
  - workflow
  - build
  - continuous integration
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires CIRCLECI_BASE_URL and CIRCLECI_API_TOKEN environment variables.
---

# Circleci-Pipelines

Manage pipelines, workflows, and jobs via CircleCI. Use when the user mentions circleci, ci, cd, pipeline, workflow, build, continuous integration.

## API Endpoints

- **GET** `/api/v2/pipeline` - List pipelines
- **POST** `/api/v2/project/{project-slug}/pipeline` - Trigger a pipeline
- **GET** `/api/v2/pipeline/{pipeline-id}` - Get pipeline by ID
- **GET** `/api/v2/pipeline/{pipeline-id}/workflow` - List workflows
- **GET** `/api/v2/workflow/{id}` - Get workflow by ID
- **POST** `/api/v2/workflow/{id}/cancel` - Cancel a workflow
- **GET** `/api/v2/workflow/{id}/job` - List jobs in workflow
- **GET** `/api/v2/project/{project-slug}` - Get project details
- **GET** `/project/{username}/{project}` - Build summary for each of the last 30 builds for a single git repo.
- **POST** `/project/{username}/{project}` - Triggers a new build, returns a summary of the build.
- **DELETE** `/project/{username}/{project}/build-cache` - Clears the cache for a project.
- **GET** `/me` - Provides information about the signed in user.
- **GET** `/projects` - List of all the projects you're following on CircleCI, with build information organized by branch.
- **GET** `/recent-builds` - Build summary for each of the last 30 recent builds, ordered by build_num.
- **POST** `/user/heroku-key` - Adds your Heroku API key to CircleCI, takes apikey as form param name.

## Actions

- list: List pipelines (GET /api/v2/pipeline)
- create: Trigger a pipeline (POST /api/v2/project/{project-slug}/pipeline)
- get_by_id: Get pipeline by ID (GET /api/v2/pipeline/{pipeline-id})
- list_workflow: List workflows (GET /api/v2/pipeline/{pipeline-id}/workflow)
- get_by_id_workflow: Get workflow by ID (GET /api/v2/workflow/{id})
- create_cancel: Cancel a workflow (POST /api/v2/workflow/{id}/cancel)
- list_job: List jobs in workflow (GET /api/v2/workflow/{id}/job)
- get_by_id_project: Get project details (GET /api/v2/project/{project-slug})
- get_by_id_project_2: Build summary for each of the last 30 builds for a single git repo. (GET /project/{username}/{project})
- create_project: Triggers a new build, returns a summary of the build. (POST /project/{username}/{project})
- delete_build_cache: Clears the cache for a project. (DELETE /project/{username}/{project}/build-cache)
- list_me: Provides information about the signed in user. (GET /me)
- list_projects: List of all the projects you're following on CircleCI, with build information or (GET /projects)
- list_recent_builds: Build summary for each of the last 30 recent builds, ordered by build_num. (GET /recent-builds)
- create_heroku_key: Adds your Heroku API key to CircleCI, takes apikey as form param name. (POST /user/heroku-key)

## Fields

- `branch`: string [OPTIONAL for trigger]
- `parameters`: object [OPTIONAL]

## Example Request Bodies

**Trigger Pipeline:**
```json
{"branch": "main", "parameters": {"deploy_env": "staging"}}
```

**Trigger Build:**
```json
{"branch": "develop"}
