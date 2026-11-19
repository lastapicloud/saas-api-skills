---
name: flyio-apps
description: 'Manage applications and machines via Fly.io. Use when the user mentions
  fly.io, flyio, app, machine, deploy, edge.

  '
version: 1.0.0
skill_type: external
base_url_env: FLYIO_BASE_URL
auth_env_var: FLYIO_API_TOKEN
auth_type: bearer
triggers:
  - fly.io
  - flyio
  - app
  - machine
  - deploy
  - edge
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires FLYIO_BASE_URL and FLYIO_API_TOKEN environment variables.
annotations:
  readOnlyHint: false
  destructiveHint: true
  idempotentHint: false
---

# Flyio-Apps

Manage applications and machines via Fly.io. Use when the user mentions fly.io, flyio, app, machine, deploy, edge.


## API Endpoints

- **GET** `/v1/apps` - List apps
- **POST** `/v1/apps` - Create app
- **GET** `/v1/apps/{app_name}` - Get app
- **DELETE** `/v1/apps/{app_name}` - Delete app
- **GET** `/v1/apps/{app_name}/machines` - List machines
- **POST** `/v1/apps/{app_name}/machines` - Create machine
- **DELETE** `/v1/apps/{app_name}/machines/{machine_id}` - Delete machine
- **POST** `/v1/apps/{app_name}/machines/{machine_id}/start` - Start machine

## Actions

- list: List apps (GET /v1/apps)
- create: Create app (POST /v1/apps)
- get_by_id: Get app (GET /v1/apps/{app_name})
- delete: Delete app (DELETE /v1/apps/{app_name})
- list_machines: List machines (GET /v1/apps/{app_name}/machines)
- create_machine: Create machine (POST /v1/apps/{app_name}/machines)
- delete_machine: Delete machine (DELETE /v1/apps/{app_name}/machines/{machine_id})
- start_machine: Start machine (POST /v1/apps/{app_name}/machines/{machine_id}/start)

## Fields

- `app_name`: string [REQUIRED for create] — App display name
- `org_slug`: string [REQUIRED for create] — Org Slug
- `config`: object [OPTIONAL for create_machine] — Config configuration

## Example Request Bodies

**Create App:**
```json
{"app_name": "my-web-app", "org_slug": "my-org"}
```

**Create Machine:**
```json
{"config": {"image": "registry.fly.io/my-web-app:latest", "guest": {"cpus": 1, "memory_mb": 256}}}
```

## Response

**App object:**
- `id`: string — Unique app identifier
- `name`: string — App name or title
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
