---
name: flyio-apps
description: Manage applications and machines via Fly.io. Use when the user mentions
  fly.io, flyio, app, machine, deploy, edge.
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
- create_machines: Create machine (POST /v1/apps/{app_name}/machines)
- delete_machines: Delete machine (DELETE /v1/apps/{app_name}/machines/{machine_id})
- create_start: Start machine (POST /v1/apps/{app_name}/machines/{machine_id}/start)

## Fields

- `app_name`: string [REQUIRED for create]
- `org_slug`: string [REQUIRED for create]
- `config`: object [OPTIONAL for create_machine]

## Example Request Bodies

**Create App:**
```json
{"app_name": "my-web-app", "org_slug": "my-org"}
```

**Create Machine:**
```json
{"config": {"image": "registry.fly.io/my-web-app:latest", "guest": {"cpus": 1, "memory_mb": 256}}}
```
