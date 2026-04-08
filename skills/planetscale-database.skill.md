---
name: planetscale-database
description: Manage databases and branches via PlanetScale. Use when the user mentions
  planetscale, database, branch, deploy request, mysql, serverless.
version: 1.0.0
skill_type: external
base_url_env: PLANETSCALE_BASE_URL
auth_env_var: PLANETSCALE_API_TOKEN
auth_type: bearer
triggers:
  - planetscale
  - database
  - branch
  - deploy request
  - mysql
  - serverless
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires PLANETSCALE_BASE_URL and PLANETSCALE_API_TOKEN environment
  variables.
---

# Planetscale-Database

Manage databases and branches via PlanetScale. Use when the user mentions planetscale, database, branch, deploy request, mysql, serverless.

## API Endpoints

- **GET** `/v1/organizations/{org}/databases` - List databases
- **POST** `/v1/organizations/{org}/databases` - Create database
- **GET** `/v1/organizations/{org}/databases/{database}` - Get database
- **DELETE** `/v1/organizations/{org}/databases/{database}` - Delete database
- **GET** `/v1/organizations/{org}/databases/{database}/branches` - List branches
- **POST** `/v1/organizations/{org}/databases/{database}/branches` - Create branch
- **GET** `/v1/organizations/{org}/databases/{database}/deploy-requests` - List deploy requests

## Actions

- list: List databases (GET /v1/organizations/{org}/databases)
- create: Create database (POST /v1/organizations/{org}/databases)
- get_by_id: Get database (GET /v1/organizations/{org}/databases/{database})
- delete: Delete database (DELETE /v1/organizations/{org}/databases/{database})
- list_branches: List branches (GET /v1/organizations/{org}/databases/{database}/branches)
- create_branches: Create branch (POST /v1/organizations/{org}/databases/{database}/branches)
- list_deploy_requests: List deploy requests (GET /v1/organizations/{org}/databases/{database}/deploy-requests)

## Fields

- `name`: string [REQUIRED for create]
- `region`: string [OPTIONAL]
- `parent_branch`: string [OPTIONAL for create_branch]

## Example Request Bodies

**Create Database:**
```json
{"name": "production-db", "region": "us-east-1"}
```

**Create Branch:**
```json
{"name": "feature/add-users-table", "parent_branch": "main"}
```
