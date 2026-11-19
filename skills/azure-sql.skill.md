---
name: azure-sql
description: "Manage Azure SQL databases and servers. Use when the user mentions azure\
  \ sql, azure database, sql server, managed instance.\n (API 2016-01-01) (API 2014-04-01)"
version: 1.0.0
skill_type: external
base_url_env: AZURE_SQL_BASE_URL
auth_env_var: AZURE_SQL_ACCESS_TOKEN
auth_type: bearer
triggers:
  - azure sql
  - azure database
  - sql server
  - managed instance
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires AZURE_SQL_BASE_URL and AZURE_SQL_ACCESS_TOKEN environment
  variables.
annotations:
  readOnlyHint: false
  destructiveHint: true
  idempotentHint: false
---

# Azure-Sql

Manage Azure SQL databases and servers. Use when the user mentions azure sql, azure database, sql server, managed instance.
 (API 2016-01-01) (API 2014-04-01)

## API Endpoints

- **GET** `/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Sql/servers/{serverName}/databases/{databaseName}/topQueries/{queryId}/queryText` - Gets a query's text.
- **GET** `/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Sql/servers/{serverName}/databases/{databaseName}/topQueries` - Gets a list of top queries by database.
- **GET** `/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Sql/servers/{serverName}/databases/{databaseName}/topQueries/{queryId}/statistics` - Lists a query's statistics.
- **GET** `/subscriptions/{subscriptionId}/providers/Microsoft.DataBoxEdge/dataBoxEdgeDevices` - Gets all the data box edge/gateway devices in a subscription.
- **PATCH** `/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.DataBoxEdge/dataBoxEdgeDevices/{deviceName}` - Modifies a Data Box Edge/Gateway resource.
- **PUT** `/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.DataBoxEdge/dataBoxEdgeDevices/{deviceName}` - Creates or updates a Data Box Edge/Gateway resource.
- **DELETE** `/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.DataBoxEdge/dataBoxEdgeDevices/{deviceName}` - Deletes the data box edge/gateway device.
- **POST** `/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.DataBoxEdge/dataBoxEdgeDevices/{deviceName}/downloadUpdates` - Downloads the updates on a data box edge/gateway device.
- **GET** `/providers/Microsoft.DataBoxEdge/operations` - List all the supported operations.
- **GET** `/subscriptions/{subscriptionId}/providers/Microsoft.Insights/webtests` - Get all Application Insights web test alerts definitions within a subscription.
- **GET** `/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Insights/components/{componentName}/webtests` - Get all Application Insights web tests defined for the specified component.
- **GET** `/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Insights/webtests` - Get all Application Insights web tests defined within a specified resource group.
- **GET** `/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Insights/webtests/{webTestName}` - Get a specific Application Insights web test definition.
- **PUT** `/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Insights/webtests/{webTestName}` - Creates or updates an Application Insights web test definition.
- **PATCH** `/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Insights/webtests/{webTestName}` - Creates or updates an Application Insights web test definition.

## Actions

- query: Gets a query's text. (GET /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Sql/servers/{serverName}/databases/{databaseName}/topQueries/{queryId}/queryText)
- list: Gets a list of top queries by database. (GET /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Sql/servers/{serverName}/databases/{databaseName}/topQueries)
- list_querys_statistics: Lists a query's statistics. (GET /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Sql/servers/{serverName}/databases/{databaseName}/topQueries/{queryId}/statistics)
- gets_data_box_edgegateway: Gets all the data box edge/gateway devices in a subscription. (GET /subscriptions/{subscriptionId}/providers/Microsoft.DataBoxEdge/dataBoxEdgeDevices)
- update: Modifies a Data Box Edge/Gateway resource. (PATCH /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.DataBoxEdge/dataBoxEdgeDevices/{deviceName})
- create_updates_data_box: Creates or updates a Data Box Edge/Gateway resource. (PUT /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.DataBoxEdge/dataBoxEdgeDevices/{deviceName})
- delete: Deletes the data box edge/gateway device. (DELETE /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.DataBoxEdge/dataBoxEdgeDevices/{deviceName})
- create: Downloads the updates on a data box edge/gateway device. (POST /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.DataBoxEdge/dataBoxEdgeDevices/{deviceName}/downloadUpdates)
- list_supported_operations: List all the supported operations. (GET /providers/Microsoft.DataBoxEdge/operations)
- get_application_insights_web: Get all Application Insights web test alerts definitions within a subscription. (GET /subscriptions/{subscriptionId}/providers/Microsoft.Insights/webtests)
- list_webtests: Get all Application Insights web tests defined for the specified component. (GET /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Insights/components/{componentName}/webtests)
- get_Microsoft.Insights_webtests: Get all Application Insights web tests defined within a specified resource group (GET /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Insights/webtests)
- get_by_id: Get a specific Application Insights web test definition. (GET /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Insights/webtests/{webTestName})
- create_updates_application_insights: Creates or updates an Application Insights web test definition. (PUT /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Insights/webtests/{webTestName})
- update_webtests: Creates or updates an Application Insights web test definition. (PATCH /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Insights/webtests/{webTestName})

## Fields

- `location`: string [REQUIRED for create] — Location
- `sku`: object [OPTIONAL] (name, tier, capacity) — Sku configuration

## Example Request Bodies

**Create or Update Database:**
```json
{"location": "eastus", "sku": {"name": "S0", "tier": "Standard", "capacity": 10}}
```

**Create Firewall Rule:**
```json
{"properties": {"startIpAddress": "203.0.113.0", "endIpAddress": "203.0.113.255"}}
```

## Response

**Webtest object:**
- `id`: string — Unique webtest identifier
- `name`: string — Webtest name or title
- `status`: string — Current status
- `type`: string — Webtest type or category
- `created_at`: string — Creation timestamp (ISO 8601)
- `updated_at`: string — Last update timestamp (ISO 8601)

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
