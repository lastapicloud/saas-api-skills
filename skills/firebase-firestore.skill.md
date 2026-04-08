---
name: firebase-firestore
description: Manage documents and collections in Firebase Cloud Firestore. Use when
  the user mentions firebase, firestore, document, collection, nosql.
version: 1.0.0
skill_type: external
base_url_env: FIREBASE_FIRESTORE_BASE_URL
auth_env_var: FIREBASE_ACCESS_TOKEN
auth_type: bearer
triggers:
  - firebase
  - firestore
  - document
  - collection
  - nosql
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires FIREBASE_FIRESTORE_BASE_URL and FIREBASE_ACCESS_TOKEN environment
  variables.
---

# Firebase-Firestore

Manage documents and collections in Firebase Cloud Firestore. Use when the user mentions firebase, firestore, document, collection, nosql.

## API Endpoints

- **GET** `/{collection_id}` - List documents in a collection
- **POST** `/{collection_id}` - Create a document
- **GET** `/{collection_id}/{document_id}` - Get a document
- **PATCH** `/{collection_id}/{document_id}` - Update a document
- **DELETE** `/{collection_id}/{document_id}` - Delete a document
- **POST** `:runQuery` - Run a structured query
- **POST** `:batchGet` - Batch get documents
- **POST** `/v1beta2/{name`
- **GET** `/v1beta2/{name`
- **GET** `/v1beta2/{parent`
- **PATCH** `/v1beta2/{field.name`
- **POST** `/v1beta2/{parent`
- **DELETE** `/v1beta2/{name`
- **POST** `/v1beta1/{name`
- **POST** `/v1beta1/{database`

## Actions

- get_by_id: List documents in a collection (GET /{collection_id})
- create_resource: Create a document (POST /{collection_id})
- get_by_id_resource: Get a document (GET /{collection_id}/{document_id})
- update: Update a document (PATCH /{collection_id}/{document_id})
- delete: Delete a document (DELETE /{collection_id}/{document_id})
- query: Run a structured query (POST :runQuery)
- create: Batch get documents (POST :batchGet)
- create_v1beta2: POST /v1beta2/{name (POST /v1beta2/{name)
- list: GET /v1beta2/{name (GET /v1beta2/{name)
- list_v1beta2: GET /v1beta2/{parent (GET /v1beta2/{parent)
- patch_v1beta2: PATCH /v1beta2/{field.name (PATCH /v1beta2/{field.name)
- create_v1beta2_2: POST /v1beta2/{parent (POST /v1beta2/{parent)
- delete_v1beta2: DELETE /v1beta2/{name (DELETE /v1beta2/{name)
- create_v1beta1: POST /v1beta1/{name (POST /v1beta1/{name)
- create_v1beta1_2: POST /v1beta1/{database (POST /v1beta1/{database)

## Fields

- `collection_id`: string [REQUIRED for collection-scoped actions] (collection name)
- `document_id`: string [REQUIRED for get, update, delete] (document ID)
- `fields`: object [REQUIRED for create, update] (document fields as Firestore value objects)
- `structuredQuery`: object [REQUIRED for run_query] (query with from, where, orderBy, limit)
- `documents`: array [REQUIRED for batch_get] (full document paths to retrieve)
- `updateMask.fieldPaths`: array [OPTIONAL for update_document] (fields to update)
- `pageSize`: integer [OPTIONAL for list_documents] (max results per page)
- `pageToken`: string [OPTIONAL for list_documents] (pagination token)

## Example Request Bodies

**Create Document:**
```json
{"fields": {"name": {"stringValue": "Jane Doe"}, "age": {"integerValue": "30"}, "active": {"booleanValue": true}}}
```

**Run Query:**
```json
{"structuredQuery": {"from": [{"collectionId": "users"}], "where": {"fieldFilter": {"field": {"fieldPath": "active"}, "op": "EQUAL", "value": {"booleanValue": true}}}, "limit": 10}}
```

**Batch Get:**
```json
{"documents": ["projects/my-project/databases/(default)/documents/users/user1", "projects/my-project/databases/(default)/documents/users/user2"]}
```
