---
name: meilisearch-search
description: "Search documents and manage indexes via the Meilisearch API. Use when\
  \ the user mentions meilisearch, search, index, document.\n (API 1.0.0)"
version: 1.0.0
skill_type: external
base_url_env: MEILISEARCH_BASE_URL
auth_env_var: MEILISEARCH_API_KEY
auth_type: bearer
triggers:
  - meilisearch
  - search
  - index
  - document
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires MEILISEARCH_BASE_URL and MEILISEARCH_API_KEY environment variables.
annotations:
  readOnlyHint: false
  destructiveHint: true
  idempotentHint: false
---

# Meilisearch-Search

Search documents and manage indexes via the Meilisearch API. Use when the user mentions meilisearch, search, index, document.
 (API 1.0.0)

## API Endpoints

- **GET** `/keys` - Get keys
- **POST** `/keys` - Create a key
- **DELETE** `/keys/kN2aK9EO8a7b627e425717d9196c8081552ca004e513545ed178f8a56981dbd3080d4a5b` - Delete a key
- **PATCH** `/keys/wYZjGJyBcdb0621b97999c233246a8ec0a35d0fcd9a6417ef8ccee0c8978b64b123af2dd` - Update a key
- **GET** `/indexes/books/search` - Search in index
- **POST** `/indexes/books/search` - Search in index
- **PATCH** `/indexes/books` - Udpate index
- **DELETE** `/indexes/books` - Delete an index
- **PUT** `/indexes/books/documents` - Add or update documents
- **GET** `/tasks` - Get all tasks
- **GET** `/tasks/0` - Get one task
- **POST** `/tasks/cancel` - Cancel tasks
- **DELETE** `/tasks` - Delete tasks
- **GET** `/stats` - Global stats
- **GET** `/version` - Version

## Actions

- list: Get keys (GET /keys)
- create: Create a key (POST /keys)
- delete_kn2ak9eo8a7b627e425717d9196c8081552ca004e513545ed178f8a56981dbd3080d4a5b: Delete a key (DELETE /keys/kN2aK9EO8a7b627e425717d9196c8081552ca004e513545ed178f8a56981dbd3080d4a5b)
- patch_wyzjgjybcdb0621b97999c233246a8ec0a35d0fcd9a6417ef8ccee0c8978b64b123af2dd: Update a key (PATCH /keys/wYZjGJyBcdb0621b97999c233246a8ec0a35d0fcd9a6417ef8ccee0c8978b64b123af2dd)
- search: Search in index (GET /indexes/books/search)
- search_index: Search in index (POST /indexes/books/search)
- patch_books: Udpate index (PATCH /indexes/books)
- delete_books: Delete an index (DELETE /indexes/books)
- put_documents: Add or update documents (PUT /indexes/books/documents)
- get_tasks: Get all tasks (GET /tasks)
- get_one_task: Get one task (GET /tasks/0)
- cancel_tasks: Cancel tasks (POST /tasks/cancel)
- delete_tasks: Delete tasks (DELETE /tasks)
- get_global_stats: Global stats (GET /stats)
- get_version: Version (GET /version)

## Fields

- `index_uid`: string [REQUIRED for search, add_documents, get_document, delete_document] (index UID) — Index U unique identifier
- `document_id`: string [REQUIRED for get_document, delete_document] (document ID) — Document unique identifier
- `q`: string [REQUIRED for search] (search query) — Q
- `limit`: integer [OPTIONAL for search] (max results to return) — Maximum number of results
- `filter`: string [OPTIONAL for search] (filter expression) — Filter criteria
- `uid`: string [REQUIRED for create_index] (index UID for creation) — U unique identifier
- `primaryKey`: string [OPTIONAL for create_index, add_documents] (primary key field name) — Primary api key or identifier

## Example Request Bodies

**Search:**
```json
{"q": "test query", "limit": 20}
```

**Create Index:**
```json
{"uid": "movies", "primaryKey": "id"}
```

**Add Documents:**
```json
[{"id": 1, "title": "Test Document", "content": "Hello from PythonREST!"}]
```

## Response

**Key object:**
- `id`: string — Unique key identifier
- `name`: string — Key name or title
- `status`: string — Current status
- `created_at`: string — Creation timestamp (ISO 8601)
- `updated_at`: string — Last update timestamp (ISO 8601)


**Required fields reference:**
```json
{
  "index_uid": "example_index_uid",
  "document_id": "example_document_id"
}
```


**Required fields reference:**
```json
{
  "index_uid": "example_index_uid",
  "document_id": "example_document_id"
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
