---
name: render-services
description: Manage Render services, deploys, and databases. Use when the user mentions
  render, service, deploy, web service.
version: 1.0.0
skill_type: external
base_url_env: RENDER_BASE_URL
auth_env_var: RENDER_API_KEY
auth_type: bearer
triggers:
  - render
  - service
  - deploy
  - web service
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires RENDER_BASE_URL and RENDER_API_KEY environment variables.
---

# Render-Services

Manage Render services, deploys, and databases. Use when the user mentions render, service, deploy, web service.

## API Endpoints

- **GET** `/v1/services` - List services
- **GET** `/v1/services/{serviceId}` - Get a service
- **POST** `/v1/services` - Create a service
- **PATCH** `/v1/services/{serviceId}` - Update a service
- **DELETE** `/v1/services/{serviceId}` - Delete a service
- **GET** `/v1/services/{serviceId}/deploys` - List deploys
- **POST** `/v1/services/{serviceId}/deploys` - Trigger a deploy
- **GET** `/v1/services/{serviceId}/deploys/{deployId}` - Get a deploy
- **GET** `/v1/services/{serviceId}/env-vars` - List env vars
- **PUT** `/v1/services/{serviceId}/env-vars` - Update env vars
- **GET** `/subscriptions/{subscriptionId}/providers/Microsoft.MixedReality/remoteRenderingAccounts` - List Remote Rendering Accounts by Subscription
- **GET** `/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.MixedReality/remoteRenderingAccounts` - List Resources by Resource Group
- **PUT** `/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.MixedReality/remoteRenderingAccounts/{accountName}` - Creating or Updating a Remote Rendering Account.
- **PATCH** `/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.MixedReality/remoteRenderingAccounts/{accountName}` - Updating a Remote Rendering Account
- **GET** `/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.MixedReality/remoteRenderingAccounts/{accountName}` - Retrieve a Remote Rendering Account.

## Actions

- list: List services (GET /v1/services)
- get_by_id: Get a service (GET /v1/services/{serviceId})
- create: Create a service (POST /v1/services)
- update: Update a service (PATCH /v1/services/{serviceId})
- delete: Delete a service (DELETE /v1/services/{serviceId})
- list_deploys: List deploys (GET /v1/services/{serviceId}/deploys)
- create_deploys: Trigger a deploy (POST /v1/services/{serviceId}/deploys)
- get_by_id_deploys: Get a deploy (GET /v1/services/{serviceId}/deploys/{deployId})
- list_env_vars: List env vars (GET /v1/services/{serviceId}/env-vars)
- put_env_vars: Update env vars (PUT /v1/services/{serviceId}/env-vars)
- list_remoterenderingaccounts: List Remote Rendering Accounts by Subscription (GET /subscriptions/{subscriptionId}/providers/Microsoft.MixedReality/remoteRenderingAccounts)
- list_remoterenderingaccounts_2: List Resources by Resource Group (GET /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.MixedReality/remoteRenderingAccounts)
- update_remoterenderingaccounts: Creating or Updating a Remote Rendering Account. (PUT /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.MixedReality/remoteRenderingAccounts/{accountName})
- update_remoterenderingaccounts_2: Updating a Remote Rendering Account (PATCH /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.MixedReality/remoteRenderingAccounts/{accountName})
- get_by_id_remoterenderingaccounts: Retrieve a Remote Rendering Account. (GET /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.MixedReality/remoteRenderingAccounts/{accountName})

## Fields

- `type`: string [REQUIRED for create] ("web_service", "static_site", "private_service", "background_worker", "cron_job")
- `name`: string [REQUIRED for create]
- `repo`: string [REQUIRED for create] (Git repo URL)
- `autoDeploy`: string [OPTIONAL] ("yes" or "no")
- `branch`: string [OPTIONAL]
- `envVars`: array of objects [OPTIONAL]

## Example Request Bodies

**Create Service:**
```json
{"type": "web_service", "name": "my-api", "repo": "https://github.com/user/repo", "autoDeploy": "yes", "branch": "main"}
```

**Update Env Vars:**
```json
[{"key": "DATABASE_URL", "value": "postgres://user:pass@host/db"}, {"key": "NODE_ENV", "value": "production"}]
```
