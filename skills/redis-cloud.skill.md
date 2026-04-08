---
name: redis-cloud
description: Manage Redis databases and subscriptions via Redis Cloud. Use when the
  user mentions redis cloud, redis, cache, database, subscription.
version: 1.0.0
skill_type: external
base_url_env: REDIS_CLOUD_BASE_URL
auth_env_var: REDIS_CLOUD_API_KEY
auth_user_env: REDIS_CLOUD_API_SECRET
auth_type: header
triggers:
  - redis cloud
  - redis
  - cache
  - database
  - subscription
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires REDIS_CLOUD_BASE_URL and REDIS_CLOUD_API_KEY environment variables.
---

# Redis-Cloud

Manage Redis databases and subscriptions via Redis Cloud. Use when the user mentions redis cloud, redis, cache, database, subscription.

## API Endpoints

- **GET** `/v1/subscriptions` - List subscriptions
- **POST** `/v1/subscriptions` - Create subscription
- **GET** `/v1/subscriptions/{subscriptionId}` - Get subscription
- **DELETE** `/v1/subscriptions/{subscriptionId}` - Delete subscription
- **GET** `/v1/subscriptions/{subscriptionId}/databases` - List databases
- **POST** `/v1/subscriptions/{subscriptionId}/databases` - Create database
- **DELETE** `/v1/subscriptions/{subscriptionId}/databases/{databaseId}` - Delete database
- **PATCH** `/v1/{name}` - Updates the metadata and configuration of a specific Redis instance. Completed longrunning.Operation will contain the
- **GET** `/v1/{name}` - Gets the latest state of a long-running operation. Clients can use this method to poll the operation result at
- **GET** `/v1/{name}/authString` - Gets the AUTH string for a Redis instance. If AUTH is not enabled for the instance the response will be empty. This
- **GET** `/v1/{name}/locations` - Lists information about the supported locations for this service.
- **GET** `/v1/{name}/operations` - Lists operations that match the specified filter in the request. If the server doesn't support this method, it returns
- **GET** `/v1/{parent}/instances` - Lists all Redis instances owned by a project in either the specified location (region) or all locations. The location
- **DELETE** `/v1/{name}` - Deletes a long-running operation. This method indicates that the client is no longer interested in the operation
- **POST** `/v1/{name}:cancel` - Starts asynchronous cancellation on a long-running operation. The server makes a best effort to cancel the operation,

## Actions

- list: List subscriptions (GET /v1/subscriptions)
- create: Create subscription (POST /v1/subscriptions)
- get_by_id: Get subscription (GET /v1/subscriptions/{subscriptionId})
- delete: Delete subscription (DELETE /v1/subscriptions/{subscriptionId})
- list_databases: List databases (GET /v1/subscriptions/{subscriptionId}/databases)
- create_databases: Create database (POST /v1/subscriptions/{subscriptionId}/databases)
- delete_databases: Delete database (DELETE /v1/subscriptions/{subscriptionId}/databases/{databaseId})
- update: Updates the metadata and configuration of a specific Redis instance. Completed l (PATCH /v1/{name})
- get_by_id_v1: Gets the latest state of a long-running operation. Clients can use this method t (GET /v1/{name})
- list_authstring: Gets the AUTH string for a Redis instance. If AUTH is not enabled for the instan (GET /v1/{name}/authString)
- list_locations: Lists information about the supported locations for this service. (GET /v1/{name}/locations)
- list_operations: Lists operations that match the specified filter in the request. If the server d (GET /v1/{name}/operations)
- list_instances: Lists all Redis instances owned by a project in either the specified location (r (GET /v1/{parent}/instances)
- delete_v1: Deletes a long-running operation. This method indicates that the client is no lo (DELETE /v1/{name})
- create_v1: Starts asynchronous cancellation on a long-running operation. The server makes a (POST /v1/{name}:cancel)

## Fields

- `name`: string [REQUIRED for create]
- `cloudAccountId`: integer [REQUIRED for create]
- `memoryLimitInGb`: number [OPTIONAL]

## Example Request Bodies

**Create Subscription:**
```json
{"name": "production-subscription", "cloudAccountId": 12345, "memoryLimitInGb": 2}
```

**Create Database:**
```json
{"name": "session-cache", "memoryLimitInGb": 1}
```
