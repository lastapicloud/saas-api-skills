---
name: remote-hr
description: Manage employees and payroll via Remote. Use when the user mentions remote,
  hr, employee, contractor, payroll, global employment.
version: 1.0.0
skill_type: external
base_url_env: REMOTE_BASE_URL
auth_env_var: REMOTE_API_TOKEN
auth_type: bearer
triggers:
  - remote
  - hr
  - employee
  - contractor
  - payroll
  - global employment
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires REMOTE_BASE_URL and REMOTE_API_TOKEN environment variables.
---

# Remote-Hr

Manage employees and payroll via Remote. Use when the user mentions remote, hr, employee, contractor, payroll, global employment.

## API Endpoints

- **GET** `/v1/employments` - List employments
- **POST** `/v1/employments` - Create employment
- **GET** `/v1/employments/{employment_id}` - Get employment
- **PATCH** `/v1/employments/{employment_id}` - Update employment
- **GET** `/v1/companies` - List companies
- **GET** `/v1/countries` - List countries
- **GET** `/v1/incentives` - List incentives
- **POST** `/v1/incentives` - Create incentive
- **GET** `/subscriptions/{subscriptionId}/providers/Microsoft.MixedReality/remoteRenderingAccounts` - List Remote Rendering Accounts by Subscription
- **GET** `/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.MixedReality/remoteRenderingAccounts` - List Resources by Resource Group
- **PUT** `/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.MixedReality/remoteRenderingAccounts/{accountName}` - Creating or Updating a Remote Rendering Account.
- **PATCH** `/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.MixedReality/remoteRenderingAccounts/{accountName}` - Updating a Remote Rendering Account
- **GET** `/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.MixedReality/remoteRenderingAccounts/{accountName}` - Retrieve a Remote Rendering Account.
- **GET** `/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.MixedReality/remoteRenderingAccounts/{accountName}/keys` - Get Both of the 2 Keys of a Remote Rendering Account
- **DELETE** `/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.MixedReality/remoteRenderingAccounts/{accountName}` - Delete a Remote Rendering Account.

## Actions

- list: List employments (GET /v1/employments)
- create: Create employment (POST /v1/employments)
- get_by_id: Get employment (GET /v1/employments/{employment_id})
- update: Update employment (PATCH /v1/employments/{employment_id})
- list_companies: List companies (GET /v1/companies)
- list_countries: List countries (GET /v1/countries)
- list_incentives: List incentives (GET /v1/incentives)
- create_incentives: Create incentive (POST /v1/incentives)
- list_remoterenderingaccounts: List Remote Rendering Accounts by Subscription (GET /subscriptions/{subscriptionId}/providers/Microsoft.MixedReality/remoteRenderingAccounts)
- list_remoterenderingaccounts_2: List Resources by Resource Group (GET /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.MixedReality/remoteRenderingAccounts)
- update_remoterenderingaccounts: Creating or Updating a Remote Rendering Account. (PUT /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.MixedReality/remoteRenderingAccounts/{accountName})
- update_remoterenderingaccounts_2: Updating a Remote Rendering Account (PATCH /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.MixedReality/remoteRenderingAccounts/{accountName})
- get_by_id_remoterenderingaccounts: Retrieve a Remote Rendering Account. (GET /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.MixedReality/remoteRenderingAccounts/{accountName})
- list_keys: Get Both of the 2 Keys of a Remote Rendering Account (GET /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.MixedReality/remoteRenderingAccounts/{accountName}/keys)
- delete: Delete a Remote Rendering Account. (DELETE /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.MixedReality/remoteRenderingAccounts/{accountName})

## Fields

- `country_code`: string [REQUIRED for create]
- `full_name`: string [REQUIRED for create]
- `job_title`: string [REQUIRED for create]
- `personal_email`: string [REQUIRED for create]

## Example Request Bodies

**Create Employment:**
```json
{"country_code": "GBR", "full_name": "Jane Smith", "job_title": "Software Engineer", "personal_email": "jane@example.com"}
```

**Update Employment:**
```json
{"job_title": "Senior Software Engineer"}
```
