---
name: monday-items
description: 'Create, search, and manage Monday.com items and boards via GraphQL.
  Use when the user mentions monday, board, monday item.

  '
version: 1.0.0
skill_type: external
base_url_env: MONDAY_BASE_URL
auth_env_var: MONDAY_API_TOKEN
auth_type: bearer
triggers:
  - monday
  - board
  - monday item
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

# Monday-Items

Create, search, and manage Monday.com items and boards via GraphQL. Use when the user mentions monday, board, monday item.


## API Endpoints

- **POST** `/graphql` - List boards (GraphQL: boards query)
- **POST** `/graphql` - Get board by ID (GraphQL: board query)
- **POST** `/graphql` - Get items (GraphQL: items query with pagination)
- **POST** `/graphql` - Get item by ID (GraphQL: items query)
- **POST** `/graphql` - Create item (GraphQL: create_item mutation)
- **POST** `/graphql` - Create subitem (GraphQL: create_subitem mutation)
- **POST** `/graphql` - Update item (GraphQL: change_column_values mutation)
- **POST** `/graphql` - Update multiple items (GraphQL: change_multiple_column_values mutation)
- **POST** `/graphql` - Delete item (GraphQL: delete_item mutation)
- **POST** `/graphql` - Duplicate item (GraphQL: duplicate_item mutation)
- **POST** `/graphql` - Archive item (GraphQL: archive_item mutation)
- **POST** `/graphql` - Search items (GraphQL: items_page_by_column_values query)
- **POST** `/graphql` - List groups (GraphQL: boards > groups query)
- **POST** `/graphql` - Get column values (GraphQL: column_values query)
- **POST** `/graphql` - Update column values (GraphQL: change_column_value mutation)

## Actions

- create: List boards (GraphQL: boards query) (POST /graphql)
- get_board_id_graphql: Get board by ID (GraphQL: board query) (POST /graphql)
- get_items_graphql_items: Get items (GraphQL: items query with pagination) (POST /graphql)
- get_item_id_graphql: Get item by ID (GraphQL: items query) (POST /graphql)
- create_item_graphql_createitem: Create item (GraphQL: create_item mutation) (POST /graphql)
- create_subitem_graphql_createsubitem: Create subitem (GraphQL: create_subitem mutation) (POST /graphql)
- update_item_graphql_changecolumnvalues: Update item (GraphQL: change_column_values mutation) (POST /graphql)
- update_multiple_items_graphql: Update multiple items (GraphQL: change_multiple_column_values mutation) (POST /graphql)
- delete_item_graphql_deleteitem: Delete item (GraphQL: delete_item mutation) (POST /graphql)
- create_graphql: Duplicate item (GraphQL: duplicate_item mutation) (POST /graphql)
- archive_item_graphql_archiveitem: Archive item (GraphQL: archive_item mutation) (POST /graphql)
- post_graphql: Search items (GraphQL: items_page_by_column_values query) (POST /graphql)
- list_groups_graphql_boards: List groups (GraphQL: boards > groups query) (POST /graphql)
- get_column_values_graphql: Get column values (GraphQL: column_values query) (POST /graphql)
- update_column_values_graphql: Update column values (GraphQL: change_column_value mutation) (POST /graphql)

## Fields

- `board_id`: integer [REQUIRED for create, update, list items] — Board unique identifier
- `item_name`: string [REQUIRED for create] — Item display name
- `column_values`: JSON string [OPTIONAL] (board column values as stringified JSON) — Column Values
- `item_id`: integer [REQUIRED for get_by_id, update, delete] — Item unique identifier
- `group_id`: string [OPTIONAL for create] (group within a board) — Group unique identifier
- `limit`: integer [OPTIONAL] (number of results to return, max 500) — Maximum number of results
- `column_id`: string [REQUIRED for search] (column ID to search by) — Column unique identifier
- `column_value`: string [REQUIRED for search] (value to search for) — Column Value
- `subitem_id`: integer [REQUIRED for subitem operations] — Subitem unique identifier
- `new_column_values`: JSON string [REQUIRED for update] (column values to set) — New Column Values
- `duplicate_to_board_id`: integer [OPTIONAL] (board to duplicate to) — Duplicate To Board unique identifier

## Example Request Bodies

**List Boards:**
```json
{"query": "{ boards(limit: 25) { id name columns { id title type } } }"}
```

**Get Board:**
```json
{"query": "{ board(ids: [123456]) { id name items_page { items { id name } } } }"}
```

**Get Item by ID:**
```json
{"query": "{ items(ids: [987654]) { id name column_values { id text } } }"}
```

**Create Item:**
```json
{"query": "mutation { create_item(board_id: 123456, group_id: \"topics\", item_name: \"New Task\", column_values: \"{\\\"status\\\": {\\\"label\\\": \\\"Working on it\\\"}}\") { id name } }"}
```

**Create Subitem:**
```json
{"query": "mutation { create_subitem(parent_id: 987654, item_name: \"Subtask\") { id name } }"}
```

**Update Item:**
```json
{"query": "mutation { change_column_values(item_id: 987654, column_values: \"{\\\"status\\\": {\\\"label\\\": \\\"Done\\\"}}\") { id name } }"}
```

**Delete Item:**
```json
{"query": "mutation { delete_item(ids: [987654]) { id } }"}
```

**Search Items:**
```json
{"query": "{ items_page_by_column_values(board_id: 123456, limit: 10, columns: [{column_id: \"status\", column_values: [\"Done\"]}]) { items { id name column_values { id text } } } }"}
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
  "subitem_id": 1,
  "new_column_values": "example_new_column_values"
}
```


**Required fields reference:**
```json
{
  "subitem_id": 1,
  "new_column_values": "example_new_column_values"
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

## Notes

Monday.com uses a GraphQL API, not REST. All requests are POST to the /graphql endpoint with a JSON body containing a `query` field. Authentication is via the `Authorization` header with a Bearer token. The `API-Version` header should be set to `2024-10` or later.
