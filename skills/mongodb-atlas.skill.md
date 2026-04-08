---
name: mongodb-atlas
description: Manage MongoDB Atlas clusters, databases, and projects. Use when the
  user mentions mongodb, atlas, cluster, database, nosql, mongo.
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
compatibility: Requires MONGODB_ATLAS_BASE_URL and MONGODB_ATLAS_PUBLIC_KEY environment
  variables.
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
- list_clusters: List clusters in a project (GET /api/atlas/v2/groups/{groupId}/clusters)
- get_by_id_clusters: Get a cluster (GET /api/atlas/v2/groups/{groupId}/clusters/{clusterName})
- create: Create a cluster (POST /api/atlas/v2/groups/{groupId}/clusters)
- delete: Delete a cluster (DELETE /api/atlas/v2/groups/{groupId}/clusters/{clusterName})
- list_databaseusers: List database users (GET /api/atlas/v2/groups/{groupId}/databaseUsers)
- create_databaseusers: Create a database user (POST /api/atlas/v2/groups/{groupId}/databaseUsers)
- list_v2: Return the Status of This MongoDB Application (GET /api/atlas/v2)
- create_groups: Create One Project (POST /api/atlas/v2/groups)
- update: Update One Project (PATCH /api/atlas/v2/groups/{groupId})
- delete_federationsettings: Delete One Federation Settings Instance (DELETE /api/atlas/v2/federationSettings/{federationSettingsId})
- update_rolemappings: Update One Role Mapping in One Organization (PUT /api/atlas/v2/federationSettings/{federationSettingsId}/connectedOrgConfigs/{orgId}/roleMappings/{id})
- list_clusters_2: Return All Authorized Clusters in All Projects (GET /api/atlas/v2/clusters)

## Fields

- `groupId`: string [REQUIRED for project-scoped actions] (project/group ID)
- `clusterName`: string [REQUIRED for get_cluster, delete_cluster] (cluster name)
- `name`: string [REQUIRED for create_cluster] (cluster name)
- `providerSettings`: object [REQUIRED for create_cluster] (cloud provider config)
- `clusterType`: string [OPTIONAL for create_cluster] (REPLICASET or SHARDED)
- `databaseName`: string [REQUIRED for create_database_user] (auth database, usually "admin")
- `username`: string [REQUIRED for create_database_user] (database username)
- `password`: string [REQUIRED for create_database_user] (database password)
- `roles`: array [REQUIRED for create_database_user] (list of role objects)

## Example Request Bodies

**Create Cluster:**
```json
{"name": "my-cluster", "clusterType": "REPLICASET", "providerSettings": {"providerName": "AWS", "regionName": "US_EAST_1", "instanceSizeName": "M10"}}
```

**Create Database User:**
```json
{"databaseName": "admin", "username": "appUser", "password": "securePass123", "roles": [{"roleName": "readWriteAnyDatabase", "databaseName": "admin"}]}
```
