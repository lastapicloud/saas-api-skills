---
name: turso-database
description: Manage databases and groups via Turso. Use when the user mentions turso,
  database, sqlite, edge database, libsql.
version: 1.0.0
skill_type: external
base_url_env: TURSO_BASE_URL
auth_env_var: TURSO_API_TOKEN
auth_type: bearer
triggers:
  - turso
  - database
  - sqlite
  - edge database
  - libsql
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires TURSO_BASE_URL and TURSO_API_TOKEN environment variables.
---

# Turso-Database

Manage databases and groups via Turso. Use when the user mentions turso, database, sqlite, edge database, libsql.

## API Endpoints

- **GET** `/v1/organizations/{org}/databases` - List databases
- **POST** `/v1/organizations/{org}/databases` - Create database
- **GET** `/v1/organizations/{org}/databases/{dbName}` - Get database
- **DELETE** `/v1/organizations/{org}/databases/{dbName}` - Delete database
- **GET** `/v1/organizations/{org}/groups` - List groups
- **POST** `/v1/organizations/{org}/groups` - Create group
- **POST** `/v1/organizations/{org}/databases/{dbName}/auth/tokens` - Create token

## Actions

- list: List databases (GET /v1/organizations/{org}/databases)
- create: Create database (POST /v1/organizations/{org}/databases)
- get_by_id: Get database (GET /v1/organizations/{org}/databases/{dbName})
- delete: Delete database (DELETE /v1/organizations/{org}/databases/{dbName})
- list_groups: List groups (GET /v1/organizations/{org}/groups)
- create_groups: Create group (POST /v1/organizations/{org}/groups)
- create_tokens: Create token (POST /v1/organizations/{org}/databases/{dbName}/auth/tokens)

## Fields

- `name`: string [REQUIRED for create]
- `group`: string [REQUIRED for create]

## Example Request Bodies

**Create Database:**
```json
{"name": "my-app-db", "group": "default"}
```

**Create Group:**
```json
{"name": "us-east-production", "location": "iad"}
