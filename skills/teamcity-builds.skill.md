---
name: teamcity-builds
description: Manage TeamCity build configurations, builds, and agents. Use when the
  user mentions teamcity, build, CI/CD, agent, configuration.
version: 1.0.0
skill_type: external
base_url_env: TEAMCITY_BASE_URL
auth_env_var: TEAMCITY_API_TOKEN
auth_type: bearer
triggers:
  - teamcity
  - build
  - CI/CD
  - agent
  - configuration
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires TEAMCITY_BASE_URL and TEAMCITY_API_TOKEN environment variables.
---

# Teamcity-Builds

Manage TeamCity build configurations, builds, and agents. Use when the user mentions teamcity, build, CI/CD, agent, configuration.

## API Endpoints

- **GET** `/app/rest/buildTypes` - List build configurations
- **GET** `/app/rest/buildTypes/{btLocator}` - Get a build configuration
- **POST** `/app/rest/buildQueue` - Trigger a build
- **GET** `/app/rest/builds` - List builds
- **GET** `/app/rest/builds/{buildLocator}` - Get a build
- **POST** `/app/rest/builds/{buildLocator}/cancel` - Cancel a build
- **GET** `/app/rest/agents` - List agents
- **GET** `/app/rest/projects` - List projects
- **POST** `/app/rest/projects` - Create a project
- **GET** `/app/rest/server` - Get server info

## Actions

- list: List build configurations (GET /app/rest/buildTypes)
- get_by_id: Get a build configuration (GET /app/rest/buildTypes/{btLocator})
- create: Trigger a build (POST /app/rest/buildQueue)
- list_builds: List builds (GET /app/rest/builds)
- get_by_id_builds: Get a build (GET /app/rest/builds/{buildLocator})
- create_cancel: Cancel a build (POST /app/rest/builds/{buildLocator}/cancel)
- list_agents: List agents (GET /app/rest/agents)
- list_projects: List projects (GET /app/rest/projects)
- create_projects: Create a project (POST /app/rest/projects)
- list_server: Get server info (GET /app/rest/server)

## Fields

- `buildType`: object [REQUIRED for trigger] with `id` (build configuration ID)
- `branchName`: string [OPTIONAL for trigger]
- `comment`: object [OPTIONAL for cancel] with `text`
- `name`: string [REQUIRED for create project]
- `parentProject`: object [OPTIONAL] with `id`

## Example Request Bodies

**Trigger Build:**
```json
{"buildType": {"id": "MyProject_Build"}, "branchName": "main"}
```

**Create Project:**
```json
{"name": "New Microservice", "parentProject": {"id": "_Root"}}
```
