---
name: monday-sales-crm
description: Manage deals, contacts, and accounts in Monday Sales CRM. Use when the
  user mentions monday sales, monday crm, monday deal, monday sales pipeline.
version: 1.0.0
skill_type: external
base_url_env: MONDAY_BASE_URL
auth_env_var: MONDAY_API_TOKEN
auth_type: bearer
triggers:
  - monday sales
  - monday crm
  - monday deal
  - monday sales pipeline
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires MONDAY_BASE_URL and MONDAY_API_TOKEN environment variables.
---

# Monday-Sales-Crm

Manage deals, contacts, and accounts in Monday Sales CRM. Use when the user mentions monday sales, monday crm, monday deal, monday sales pipeline.

## API Endpoints

- **POST** `/graphql` - List CRM boards (GraphQL: boards query with workspace filter)
- **POST** `/graphql` - Get CRM board (GraphQL: board query)
- **POST** `/graphql` - Get CRM items (GraphQL: items_page query with pagination)
- **POST** `/graphql` - Get item by ID (GraphQL: items query)
- **POST** `/graphql` - Create CRM item (GraphQL: create_item mutation)
- **POST** `/graphql` - Update CRM item (GraphQL: change_column_values mutation)
- **POST** `/graphql` - Bulk update items (GraphQL: change_multiple_column_values mutation)
- **POST** `/graphql` - Delete CRM item (GraphQL: delete_item mutation)
- **POST** `/graphql` - Duplicate item (GraphQL: duplicate_item mutation)
- **POST** `/graphql` - Move item to group (GraphQL: move_item_to_group mutation)
- **POST** `/graphql` - Move item to board (GraphQL: move_item_to_board mutation)
- **POST** `/graphql` - List groups in board (GraphQL: boards > groups query)
- **POST** `/graphql` - Search items (GraphQL: items_page_by_column_values query)
- **POST** `/graphql` - Create webhook (GraphQL: create_webhook mutation)
- **POST** `/graphql` - Get item subscribers (GraphQL: items subscribers query)

## Actions

- create: List CRM boards (GraphQL: boards query with workspace filter) (POST /graphql)
- create_graphql: Get CRM board (GraphQL: board query) (POST /graphql)
- create_graphql_2: Get CRM items (GraphQL: items_page query with pagination) (POST /graphql)
- create_graphql_3: Get item by ID (GraphQL: items query) (POST /graphql)
- create_graphql_4: Create CRM item (GraphQL: create_item mutation) (POST /graphql)
- create_graphql_5: Update CRM item (GraphQL: change_column_values mutation) (POST /graphql)
- create_graphql_6: Bulk update items (GraphQL: change_multiple_column_values mutation) (POST /graphql)
- create_graphql_7: Delete CRM item (GraphQL: delete_item mutation) (POST /graphql)
- create_graphql_8: Duplicate item (GraphQL: duplicate_item mutation) (POST /graphql)
- create_graphql_9: Move item to group (GraphQL: move_item_to_group mutation) (POST /graphql)
- create_graphql_10: Move item to board (GraphQL: move_item_to_board mutation) (POST /graphql)
- create_graphql_11: List groups in board (GraphQL: boards > groups query) (POST /graphql)
- create_graphql_12: Search items (GraphQL: items_page_by_column_values query) (POST /graphql)
- create_graphql_13: Create webhook (GraphQL: create_webhook mutation) (POST /graphql)
- create_graphql_14: Get item subscribers (GraphQL: items subscribers query) (POST /graphql)

## Fields

- `board_id`: integer [REQUIRED for list_items, create_item, list_groups] (board ID)
- `item_id`: integer [REQUIRED for update_item, delete_item, move_item] (item ID)
- `group_id`: string [REQUIRED for create_item, move_item] (group/stage ID)
- `item_name`: string [REQUIRED for create_item] (item name)
- `column_values`: JSON string [OPTIONAL] (column values as JSON)
- `workspace_id`: integer [OPTIONAL] (workspace ID for filtering boards)
- `limit`: integer [OPTIONAL] (number of results to return)
- `cursor`: string [OPTIONAL] (pagination cursor for items_page)
- `column_id`: string [REQUIRED for search items] (column ID to search by)
- `column_value`: string [REQUIRED for search items] (value to search for)

## Example Request Bodies

**List Boards:**
```json
{"query": "{ boards(limit: 25) { id name } }"}
```

**Create Item:**
```json
{"query": "mutation { create_item(board_id: 123, group_id: \"new_group\", item_name: \"New Deal\") { id name } }"}
```
