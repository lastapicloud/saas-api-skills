---
name: teamcity-builds
description: 'Manage TeamCity build configurations, builds, and agents. Use when the
  user mentions teamcity, build, CI/CD, agent, configuration.

  '
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
annotations:
  readOnlyHint: false
  destructiveHint: false
  idempotentHint: false
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
- get_build: Get a build (GET /app/rest/builds/{buildLocator})
- cancel_build: Cancel a build (POST /app/rest/builds/{buildLocator}/cancel)
- list_agents: List agents (GET /app/rest/agents)
- list_projects: List projects (GET /app/rest/projects)
- create_project: Create a project (POST /app/rest/projects)
- get_server_info: Get server info (GET /app/rest/server)

## Fields

- `buildType`: object [REQUIRED for trigger] with `id` (build configuration ID) — Build resource type
- `branchName`: string [OPTIONAL for trigger] — Branch display name
- `comment`: object [OPTIONAL for cancel] with `text` — Comment configuration
- `name`: string [REQUIRED for create project] — Display name
- `parentProject`: object [OPTIONAL] with `id` — Parentproject configuration

## Example Request Bodies

**Trigger Build:**
```json
{"buildType": {"id": "MyProject_Build"}, "branchName": "main"}
```

**Create Project:**
```json
{"name": "New Microservice", "parentProject": {"id": "_Root"}}
```

## Response

**Buildtype object:**
- `id`: string — Unique buildtype identifier
- `name`: string — Buildtype name or title
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
