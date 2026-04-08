---
name: azure-sql
description: Manage Azure SQL databases and servers. Use when the user mentions azure
  sql, azure database, sql server, managed instance.
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
---

# Azure-Sql

Manage Azure SQL databases and servers. Use when the user mentions azure sql, azure database, sql server, managed instance.

## API Endpoints

- **GET** `/subscriptions/{subscriptionId}/providers/Microsoft.Sql/servers` - List servers
- **GET** `/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Sql/servers/{serverName}/databases` - List databases
- **PUT** `/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Sql/servers/{serverName}/databases/{databaseName}` - Create or update database
- **DELETE** `/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Sql/servers/{serverName}/databases/{databaseName}` - Delete database
- **GET** `/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Sql/servers/{serverName}/databases/{databaseName}` - Get database
- **GET** `/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Sql/servers/{serverName}/firewallRules` - List firewall rules
- **PUT** `/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Sql/servers/{serverName}/firewallRules/{firewallRuleName}` - Create firewall rule
- **GET** `/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.DBforPostgreSQL/servers/{serverName}/keys` - Gets a list of  Server keys.
- **GET** `/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.DBforPostgreSQL/servers/{serverName}/keys/{keyName}` - Gets a PostgreSQL Server key.
- **PUT** `/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.DBforPostgreSQL/servers/{serverName}/keys/{keyName}` - Creates or updates a PostgreSQL Server key.
- **DELETE** `/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.DBforPostgreSQL/servers/{serverName}/keys/{keyName}` - Deletes the PostgreSQL Server key with the given name.
- **GET** `/providers/microsoft.insights/operations` - Lists all of the available operations from Microsoft.Insights provider.
- **GET** `/subscriptions/{subscriptionId}/providers/Microsoft.Subscriptions.Admin/locations/{location}/quotas` - Get the list of quotas at a location.

## Actions

- list: List servers (GET /subscriptions/{subscriptionId}/providers/Microsoft.Sql/servers)
- list_databases: List databases (GET /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Sql/servers/{serverName}/databases)
- update: Create or update database (PUT /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Sql/servers/{serverName}/databases/{databaseName})
- delete: Delete database (DELETE /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Sql/servers/{serverName}/databases/{databaseName})
- get_by_id: Get database (GET /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Sql/servers/{serverName}/databases/{databaseName})
- list_firewallrules: List firewall rules (GET /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Sql/servers/{serverName}/firewallRules)
- update_firewallrules: Create firewall rule (PUT /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Sql/servers/{serverName}/firewallRules/{firewallRuleName})
- list_keys: Gets a list of  Server keys. (GET /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.DBforPostgreSQL/servers/{serverName}/keys)
- get_by_id_keys: Gets a PostgreSQL Server key. (GET /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.DBforPostgreSQL/servers/{serverName}/keys/{keyName})
- update_keys: Creates or updates a PostgreSQL Server key. (PUT /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.DBforPostgreSQL/servers/{serverName}/keys/{keyName})
- delete_keys: Deletes the PostgreSQL Server key with the given name. (DELETE /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.DBforPostgreSQL/servers/{serverName}/keys/{keyName})
- list_operations: Lists all of the available operations from Microsoft.Insights provider. (GET /providers/microsoft.insights/operations)
- list_quotas: Get the list of quotas at a location. (GET /subscriptions/{subscriptionId}/providers/Microsoft.Subscriptions.Admin/locations/{location}/quotas)

## Fields

- `location`: string [REQUIRED for create]
- `sku`: object [OPTIONAL] (name, tier, capacity)

## Example Request Bodies

**Create or Update Database:**
```json
{"location": "eastus", "sku": {"name": "S0", "tier": "Standard", "capacity": 10}}
```

**Create Firewall Rule:**
```json
{"properties": {"startIpAddress": "203.0.113.0", "endIpAddress": "203.0.113.255"}}
```
