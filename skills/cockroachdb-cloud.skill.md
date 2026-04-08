---
name: cockroachdb-cloud
description: Manage CockroachDB clusters and databases via CockroachDB Cloud. Use
  when the user mentions cockroachdb cloud, cockroach, cluster, serverless, database.
version: 1.0.0
skill_type: external
base_url_env: COCKROACHDB_CLOUD_BASE_URL
auth_env_var: COCKROACHDB_CLOUD_API_KEY
auth_type: bearer
triggers:
  - cockroachdb cloud
  - cockroach
  - cluster
  - serverless
  - database
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires COCKROACHDB_CLOUD_BASE_URL and COCKROACHDB_CLOUD_API_KEY environment
  variables.
---

# Cockroachdb-Cloud

Manage CockroachDB clusters and databases via CockroachDB Cloud. Use when the user mentions cockroachdb cloud, cockroach, cluster, serverless, database.

## API Endpoints

- **GET** `/api/v1/clusters` - List clusters
- **POST** `/api/v1/clusters` - Create a cluster
- **GET** `/api/v1/clusters/{cluster_id}` - Get cluster by ID
- **DELETE** `/api/v1/clusters/{cluster_id}` - Delete a cluster
- **PATCH** `/api/v1/clusters/{cluster_id}` - Update a cluster
- **GET** `/api/v1/clusters/{cluster_id}/databases` - List databases
- **POST** `/api/v1/clusters/{cluster_id}/sql-users` - Create a SQL user
- **GET** `/api/v1/clusters/{cluster_id}/sql-users` - List SQL users

## Actions

- list: List clusters (GET /api/v1/clusters)
- create: Create a cluster (POST /api/v1/clusters)
- get_by_id: Get cluster by ID (GET /api/v1/clusters/{cluster_id})
- delete: Delete a cluster (DELETE /api/v1/clusters/{cluster_id})
- update: Update a cluster (PATCH /api/v1/clusters/{cluster_id})
- list_databases: List databases (GET /api/v1/clusters/{cluster_id}/databases)
- create_sql_users: Create a SQL user (POST /api/v1/clusters/{cluster_id}/sql-users)
- list_sql_users: List SQL users (GET /api/v1/clusters/{cluster_id}/sql-users)

## Fields

- `name`: string [REQUIRED for create]
- `provider`: string [REQUIRED for create] (GCP, AWS, AZURE)
- `spec`: object [REQUIRED for create]

## Example Request Bodies

**Create Cluster:**
```json
{"name": "my-cluster", "provider": "GCP", "spec": {"serverless": {"regions": ["us-central1"]}}}
```

**Create SQL User:**
```json
{"name": "app_user", "password": "securePass123!"}
