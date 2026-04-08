---
name: aiven-cloud
description: Manage cloud database services via Aiven. Use when the user mentions
  aiven, cloud database, managed database, kafka, postgresql, redis.
version: 1.0.0
skill_type: external
base_url_env: AIVEN_BASE_URL
auth_env_var: AIVEN_API_TOKEN
auth_type: bearer
triggers:
  - aiven
  - cloud database
  - managed database
  - kafka
  - postgresql
  - redis
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires AIVEN_BASE_URL and AIVEN_API_TOKEN environment variables.
---

# Aiven-Cloud

Manage cloud database services via Aiven. Use when the user mentions aiven, cloud database, managed database, kafka, postgresql, redis.

## API Endpoints

- **GET** `/v1/project` - List projects
- **GET** `/v1/project/{project}/service` - List services
- **POST** `/v1/project/{project}/service` - Create a service
- **GET** `/v1/project/{project}/service/{service_name}` - Get service details
- **PUT** `/v1/project/{project}/service/{service_name}` - Update a service
- **DELETE** `/v1/project/{project}/service/{service_name}` - Delete a service
- **GET** `/v1/project/{project}/service/{service_name}/db` - List databases
- **POST** `/v1/project/{project}/service/{service_name}/db` - Create a database

## Actions

- list: List projects (GET /v1/project)
- list_service: List services (GET /v1/project/{project}/service)
- create: Create a service (POST /v1/project/{project}/service)
- get_by_id: Get service details (GET /v1/project/{project}/service/{service_name})
- update: Update a service (PUT /v1/project/{project}/service/{service_name})
- delete: Delete a service (DELETE /v1/project/{project}/service/{service_name})
- list_db: List databases (GET /v1/project/{project}/service/{service_name}/db)
- create_db: Create a database (POST /v1/project/{project}/service/{service_name}/db)

## Fields

- `service_name`: string [REQUIRED for create]
- `service_type`: string [REQUIRED for create]
- `plan`: string [REQUIRED for create]
- `cloud`: string [REQUIRED for create]

## Example Request Bodies

**Create Service:**
```json
{"service_name": "my-postgresql", "service_type": "pg", "plan": "business-4", "cloud": "google-europe-west1"}
```

**Update Service:**
```json
{"plan": "business-8", "cloud": "google-europe-west1"}
