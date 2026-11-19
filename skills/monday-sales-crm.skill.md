---
name: monday-sales-crm
description: 'Manage deals, contacts, and accounts in Monday Sales CRM. Use when the
  user mentions monday sales, monday crm, monday deal, monday sales pipeline.

  '
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
annotations:
  readOnlyHint: false
  destructiveHint: false
  idempotentHint: false
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
- get_crm_board_graphql: Get CRM board (GraphQL: board query) (POST /graphql)
- get_crm_items_graphql: Get CRM items (GraphQL: items_page query with pagination) (POST /graphql)
- get_item_id_graphql: Get item by ID (GraphQL: items query) (POST /graphql)
- create_crm_item_graphql: Create CRM item (GraphQL: create_item mutation) (POST /graphql)
- update_crm_item_graphql: Update CRM item (GraphQL: change_column_values mutation) (POST /graphql)
- create_bulk_update_items_graphql: Bulk update items (GraphQL: change_multiple_column_values mutation) (POST /graphql)
- delete_crm_item_graphql: Delete CRM item (GraphQL: delete_item mutation) (POST /graphql)
- create_graphql: Duplicate item (GraphQL: duplicate_item mutation) (POST /graphql)
- move_item_group_graphql: Move item to group (GraphQL: move_item_to_group mutation) (POST /graphql)
- move_item_board_graphql: Move item to board (GraphQL: move_item_to_board mutation) (POST /graphql)
- list_groups_board_graphql: List groups in board (GraphQL: boards > groups query) (POST /graphql)
- post_graphql: Search items (GraphQL: items_page_by_column_values query) (POST /graphql)
- create_webhook_graphql_createwebhook: Create webhook (GraphQL: create_webhook mutation) (POST /graphql)
- get_item_subscribers_graphql: Get item subscribers (GraphQL: items subscribers query) (POST /graphql)

## Fields

- `board_id`: integer [REQUIRED for list_items, create_item, list_groups] (board ID) — Board unique identifier
- `item_id`: integer [REQUIRED for update_item, delete_item, move_item] (item ID) — Item unique identifier
- `group_id`: string [REQUIRED for create_item, move_item] (group/stage ID) — Group unique identifier
- `item_name`: string [REQUIRED for create_item] (item name) — Item display name
- `column_values`: JSON string [OPTIONAL] (column values as JSON) — Column Values
- `workspace_id`: integer [OPTIONAL] (workspace ID for filtering boards) — Workspace unique identifier
- `limit`: integer [OPTIONAL] (number of results to return) — Maximum number of results
- `cursor`: string [OPTIONAL] (pagination cursor for items_page) — Pagination cursor
- `column_id`: string [REQUIRED for search items] (column ID to search by) — Column unique identifier
- `column_value`: string [REQUIRED for search items] (value to search for) — Column Value

## Example Request Bodies

**List Boards:**
```json
{"query": "{ boards(limit: 25) { id name } }"}
```

**Create Item:**
```json
{"query": "mutation { create_item(board_id: 123, group_id: \"new_group\", item_name: \"New Deal\") { id name } }"}
```

## Response

**Graphql object:**
- `id`: string — Unique graphql identifier
- `name`: string — Graphql name or title
- `status`: string — Current status
- `created_at`: string — Creation timestamp (ISO 8601)
- `updated_at`: string — Last update timestamp (ISO 8601)


**Required fields reference:**
```json
{
  "item_id": 1,
  "column_id": "example_column_id",
  "column_value": "example_column_value"
}
```


**Required fields reference:**
```json
{
  "item_id": 1,
  "column_id": "example_column_id",
  "column_value": "example_column_value"
}
```

## Error Responses

| Status | Meaning |
|--------|---------|
| 400 | Invalid request body — check required fields and types |
| 401 | Authentication failed — verify API key or token is valid and not expired |
| 403 | Forbidden — insufficient permissions or scope for this action |
| 409 | Conflict — resource already exists or concurrent modification |
| 429 | Rate limited — too many requests, retry after delay |
| 500 | Server error — retry or check service status page |
