---
name: meilisearch-search
description: Search documents and manage indexes via the Meilisearch API. Use when
  the user mentions meilisearch, search, index, document.
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
---

# Meilisearch-Search

Search documents and manage indexes via the Meilisearch API. Use when the user mentions meilisearch, search, index, document.

## API Endpoints

- **POST** `/indexes/{index_uid}/search` - Search documents in an index
- **POST** `/indexes/{index_uid}/documents` - Add or update documents
- **GET** `/indexes/{index_uid}/documents/{document_id}` - Get a document by ID
- **DELETE** `/indexes/{index_uid}/documents/{document_id}` - Delete a document
- **GET** `/indexes` - List all indexes
- **POST** `/indexes` - Create an index
- **GET** `/keys` - Get keys
- **POST** `/keys` - Create a key
- **DELETE** `/keys/kN2aK9EO8a7b627e425717d9196c8081552ca004e513545ed178f8a56981dbd3080d4a5b` - Delete a key
- **PATCH** `/keys/wYZjGJyBcdb0621b97999c233246a8ec0a35d0fcd9a6417ef8ccee0c8978b64b123af2dd` - Update a key
- **GET** `/indexes/books/search` - Search in index
- **POST** `/indexes/books/search` - Search in index
- **PATCH** `/indexes/books` - Udpate index
- **DELETE** `/indexes/books` - Delete an index
- **PUT** `/indexes/books/documents` - Add or update documents

## Actions

- search: Search documents in an index (POST /indexes/{index_uid}/search)
- create: Add or update documents (POST /indexes/{index_uid}/documents)
- get_by_id: Get a document by ID (GET /indexes/{index_uid}/documents/{document_id})
- delete: Delete a document (DELETE /indexes/{index_uid}/documents/{document_id})
- list: List all indexes (GET /indexes)
- create_indexes: Create an index (POST /indexes)
- list_keys: Get keys (GET /keys)
- create_keys: Create a key (POST /keys)
- delete_kn2ak9eo8a7b627e425717d9196c8081552ca004e513545ed178f8a56981dbd3080d4a5b: Delete a key (DELETE /keys/kN2aK9EO8a7b627e425717d9196c8081552ca004e513545ed178f8a56981dbd3080d4a5b)
- patch_wyzjgjybcdb0621b97999c233246a8ec0a35d0fcd9a6417ef8ccee0c8978b64b123af2dd: Update a key (PATCH /keys/wYZjGJyBcdb0621b97999c233246a8ec0a35d0fcd9a6417ef8ccee0c8978b64b123af2dd)
- search_books: Search in index (GET /indexes/books/search)
- search_books_2: Search in index (POST /indexes/books/search)
- patch_books: Udpate index (PATCH /indexes/books)
- delete_books: Delete an index (DELETE /indexes/books)
- put_documents: Add or update documents (PUT /indexes/books/documents)

## Fields

- `index_uid`: string [REQUIRED for search, add_documents, get_document, delete_document] (index UID)
- `document_id`: string [REQUIRED for get_document, delete_document] (document ID)
- `q`: string [REQUIRED for search] (search query)
- `limit`: integer [OPTIONAL for search] (max results to return)
- `filter`: string [OPTIONAL for search] (filter expression)
- `uid`: string [REQUIRED for create_index] (index UID for creation)
- `primaryKey`: string [OPTIONAL for create_index, add_documents] (primary key field name)

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
