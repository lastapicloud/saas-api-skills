---
name: google-cloud-sql
description: Manage Cloud SQL instances and databases via Google Cloud. Use when the
  user mentions google cloud sql, cloud sql, sql instance, database.
version: 1.0.0
skill_type: external
base_url_env: GOOGLE_CLOUD_SQL_BASE_URL
auth_env_var: GOOGLE_API_TOKEN
auth_type: bearer
triggers:
  - google cloud sql
  - cloud sql
  - sql instance
  - database
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires GOOGLE_CLOUD_SQL_BASE_URL and GOOGLE_API_TOKEN environment
  variables.
---

# Google-Cloud-Sql

Manage Cloud SQL instances and databases via Google Cloud. Use when the user mentions google cloud sql, cloud sql, sql instance, database.

## API Endpoints

- **GET** `/v1/projects/{project}/instances` - List instances
- **POST** `/v1/projects/{project}/instances` - Create instance
- **GET** `/v1/projects/{project}/instances/{instance}` - Get instance
- **DELETE** `/v1/projects/{project}/instances/{instance}` - Delete instance
- **PATCH** `/v1/projects/{project}/instances/{instance}` - Update instance
- **GET** `/v1/projects/{project}/instances/{instance}/databases` - List databases
- **POST** `/v1/projects/{project}/instances/{instance}/databases` - Create database

## Actions

- list: List instances (GET /v1/projects/{project}/instances)
- create: Create instance (POST /v1/projects/{project}/instances)
- get_by_id: Get instance (GET /v1/projects/{project}/instances/{instance})
- delete: Delete instance (DELETE /v1/projects/{project}/instances/{instance})
- update: Update instance (PATCH /v1/projects/{project}/instances/{instance})
- list_databases: List databases (GET /v1/projects/{project}/instances/{instance}/databases)
- create_databases: Create database (POST /v1/projects/{project}/instances/{instance}/databases)

## Fields

- `name`: string [REQUIRED for create]
- `databaseVersion`: string [REQUIRED for create]
- `settings`: object [REQUIRED for create] (tier, etc.)

## Example Request Bodies

**Create Instance:**
```json
{"name": "my-sql-instance", "databaseVersion": "MYSQL_8_0", "settings": {"tier": "db-f1-micro"}}
```

**Create Database:**
```json
{"name": "app_database", "charset": "utf8mb4"}
