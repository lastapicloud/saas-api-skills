---
name: treblle-monitoring
description: Monitor APIs and track requests via Treblle. Use when the user mentions
  treblle, api monitoring, api analytics, request, observability.
version: 1.0.0
skill_type: external
base_url_env: TREBLLE_BASE_URL
auth_env_var: TREBLLE_API_TOKEN
auth_type: bearer
triggers:
  - treblle
  - api monitoring
  - api analytics
  - request
  - observability
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires TREBLLE_BASE_URL and TREBLLE_API_TOKEN environment variables.
---

# Treblle-Monitoring

Monitor APIs and track requests via Treblle. Use when the user mentions treblle, api monitoring, api analytics, request, observability.

## API Endpoints

- **GET** `/v1/projects` - List projects
- **POST** `/v1/projects` - Create project
- **GET** `/v1/projects/{projectId}` - Get project
- **GET** `/v1/projects/{projectId}/requests` - List requests
- **GET** `/v1/projects/{projectId}/endpoints` - List endpoints
- **GET** `/v1/projects/{projectId}/errors` - List errors

## Actions

- list: List projects (GET /v1/projects)
- create: Create project (POST /v1/projects)
- get_by_id: Get project (GET /v1/projects/{projectId})
- list_requests: List requests (GET /v1/projects/{projectId}/requests)
- list_endpoints: List endpoints (GET /v1/projects/{projectId}/endpoints)
- list_errors: List errors (GET /v1/projects/{projectId}/errors)

## Fields

- `name`: string [REQUIRED for create]
- `base_url`: string [OPTIONAL]

## Example Request Bodies

**Create Project:**
```json
{"name": "Production API", "base_url": "https://api.example.com"}
```

**List Requests (query parameters):**
```json
{"projectId": "proj_abc123"}
