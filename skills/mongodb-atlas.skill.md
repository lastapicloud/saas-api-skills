---
name: mongodb-atlas
description: 'Manage MongoDB Atlas clusters, databases, and projects. Use when the
  user mentions mongodb, atlas, cluster, database, nosql, mongo.

  '
version: 1.0.0
skill_type: external
base_url_env: MONGODB_ATLAS_BASE_URL
auth_env_var: MONGODB_ATLAS_PUBLIC_KEY
auth_type: digest
triggers:
  - mongodb
  - atlas
  - cluster
  - database
  - nosql
  - mongo
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: 'Requires MONGODB_ATLAS_BASE_URL and MONGODB_ATLAS_PUBLIC_KEY environment
  variables.

  '
annotations:
  readOnlyHint: false
  destructiveHint: true
  idempotentHint: false
---

# Mongodb-Atlas

Manage MongoDB Atlas clusters, databases, and projects. Use when the user mentions mongodb, atlas, cluster, database, nosql, mongo.


## API Endpoints

- **GET** `/api/atlas/v2/groups` - List projects
- **GET** `/api/atlas/v2/groups/{groupId}` - Get a project
- **GET** `/api/atlas/v2/groups/{groupId}/clusters` - List clusters in a project
- **GET** `/api/atlas/v2/groups/{groupId}/clusters/{clusterName}` - Get a cluster
- **POST** `/api/atlas/v2/groups/{groupId}/clusters` - Create a cluster
- **DELETE** `/api/atlas/v2/groups/{groupId}/clusters/{clusterName}` - Delete a cluster
- **GET** `/api/atlas/v2/groups/{groupId}/databaseUsers` - List database users
- **POST** `/api/atlas/v2/groups/{groupId}/databaseUsers` - Create a database user
- **GET** `/api/atlas/v2` - Return the Status of This MongoDB Application
- **POST** `/api/atlas/v2/groups` - Create One Project
- **PATCH** `/api/atlas/v2/groups/{groupId}` - Update One Project
- **DELETE** `/api/atlas/v2/federationSettings/{federationSettingsId}` - Delete One Federation Settings Instance
- **PUT** `/api/atlas/v2/federationSettings/{federationSettingsId}/connectedOrgConfigs/{orgId}/roleMappings/{id}` - Update One Role Mapping in One Organization
- **GET** `/api/atlas/v2/clusters` - Return All Authorized Clusters in All Projects

## Actions

- list: List projects (GET /api/atlas/v2/groups)
- get_by_id: Get a project (GET /api/atlas/v2/groups/{groupId})
- list_clusters_project: List clusters in a project (GET /api/atlas/v2/groups/{groupId}/clusters)
- get_cluster: Get a cluster (GET /api/atlas/v2/groups/{groupId}/clusters/{clusterName})
- create: Create a cluster (POST /api/atlas/v2/groups/{groupId}/clusters)
- delete: Delete a cluster (DELETE /api/atlas/v2/groups/{groupId}/clusters/{clusterName})
- list_database_users: List database users (GET /api/atlas/v2/groups/{groupId}/databaseUsers)
- create_database_user: Create a database user (POST /api/atlas/v2/groups/{groupId}/databaseUsers)
- get_return_status_this_mongodb: Return the Status of This MongoDB Application (GET /api/atlas/v2)
- create_one_project: Create One Project (POST /api/atlas/v2/groups)
- update: Update One Project (PATCH /api/atlas/v2/groups/{groupId})
- delete_one_federation_settings: Delete One Federation Settings Instance (DELETE /api/atlas/v2/federationSettings/{federationSettingsId})
- update_one_role_mapping: Update One Role Mapping in One Organization (PUT /api/atlas/v2/federationSettings/{federationSettingsId}/connectedOrgConfigs/{orgId}/roleMappings/{id})
- get_return_authorized_clusters_projects: Return All Authorized Clusters in All Projects (GET /api/atlas/v2/clusters)

## Fields

- `groupId`: string [REQUIRED for project-scoped actions] (project/group ID) — Group unique identifier
- `clusterName`: string [REQUIRED for get_cluster, delete_cluster] (cluster name) — Cluster display name
- `name`: string [REQUIRED for create_cluster] (cluster name) — Display name
- `providerSettings`: object [REQUIRED for create_cluster] (cloud provider config) — Providersettings configuration
- `clusterType`: string [OPTIONAL for create_cluster] (REPLICASET or SHARDED) — Cluster resource type
- `databaseName`: string [REQUIRED for create_database_user] (auth database, usually "admin") — Database display name
- `username`: string [REQUIRED for create_database_user] (database username) — Username
- `password`: string [REQUIRED for create_database_user] (database password) — Password
- `roles`: array [REQUIRED for create_database_user] (list of role objects) — List of roles

## Example Request Bodies

**Create Cluster:**
```json
{"name": "my-cluster", "clusterType": "REPLICASET", "providerSettings": {"providerName": "AWS", "regionName": "US_EAST_1", "instanceSizeName": "M10"}}
```

**Create Database User:**
```json
{"databaseName": "admin", "username": "appUser", "password": "securePass123", "roles": [{"roleName": "readWriteAnyDatabase", "databaseName": "admin"}]}
```

## Response

**Cluster object:**
- `id`: string — Unique cluster identifier
- `name`: string — Cluster name or title
- `status`: string — Current status
- `created_at`: string — Creation timestamp (ISO 8601)
- `updated_at`: string — Last update timestamp (ISO 8601)


**Required fields reference:**
```json
{
  "groupId": "example_groupId",
  "clusterName": "example_clusterName"
}
```


**Required fields reference:**
```json
{
  "groupId": "example_groupId",
  "clusterName": "example_clusterName"
}
```

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
