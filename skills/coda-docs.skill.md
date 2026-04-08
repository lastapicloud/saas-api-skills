---
name: coda-docs
description: Manage docs, tables, and rows via Coda. Use when the user mentions coda,
  doc, table, row, formula, page.
version: 1.0.0
skill_type: external
base_url_env: CODA_BASE_URL
auth_env_var: CODA_API_TOKEN
auth_type: bearer
triggers:
  - coda
  - doc
  - table
  - row
  - formula
  - page
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires CODA_BASE_URL and CODA_API_TOKEN environment variables.
---

# Coda-Docs

Manage docs, tables, and rows via Coda. Use when the user mentions coda, doc, table, row, formula, page.

## API Endpoints

- **GET** `/v1/docs` - List docs
- **POST** `/v1/docs` - Create a doc
- **GET** `/v1/docs/{docId}` - Get doc by ID
- **GET** `/v1/docs/{docId}/tables` - List tables
- **GET** `/v1/docs/{docId}/tables/{tableIdOrName}/rows` - List rows
- **POST** `/v1/docs/{docId}/tables/{tableIdOrName}/rows` - Upsert rows
- **DELETE** `/v1/docs/{docId}/tables/{tableIdOrName}/rows/{rowIdOrName}` - Delete a row
- **GET** `/v1/docs/{docId}/pages` - List pages
- **GET** `/companies/{companyId}/sync/expenses/config` - Get company configuration
- **GET** `/companies/{companyId}/sync/expenses/mappingOptions` - Mapping options
- **POST** `/companies/{companyId}/sync/expenses/config` - Set company configuration
- **POST** `/companies/{companyId}/sync/expenses/syncs` - Initiate sync
- **GET** `/companies/{companyId}/sync/expenses/syncs/{syncId}/transactions` - Get Sync transactions
- **GET** `/companies/{companyId}/sync/expenses/syncs/{syncId}/transactions/{transactionId}` - Get Sync Transaction
- **POST** `/companies/{companyId}/sync/expenses/connections/partnerExpense` - Create Partner Expense connection

## Actions

- list: List docs (GET /v1/docs)
- create: Create a doc (POST /v1/docs)
- get_by_id: Get doc by ID (GET /v1/docs/{docId})
- list_tables: List tables (GET /v1/docs/{docId}/tables)
- list_rows: List rows (GET /v1/docs/{docId}/tables/{tableIdOrName}/rows)
- create_rows: Upsert rows (POST /v1/docs/{docId}/tables/{tableIdOrName}/rows)
- delete: Delete a row (DELETE /v1/docs/{docId}/tables/{tableIdOrName}/rows/{rowIdOrName})
- list_pages: List pages (GET /v1/docs/{docId}/pages)
- list_config: Get company configuration (GET /companies/{companyId}/sync/expenses/config)
- list_mappingoptions: Mapping options (GET /companies/{companyId}/sync/expenses/mappingOptions)
- create_config: Set company configuration (POST /companies/{companyId}/sync/expenses/config)
- create_syncs: Initiate sync (POST /companies/{companyId}/sync/expenses/syncs)
- list_transactions: Get Sync transactions (GET /companies/{companyId}/sync/expenses/syncs/{syncId}/transactions)
- get_by_id_transactions: Get Sync Transaction (GET /companies/{companyId}/sync/expenses/syncs/{syncId}/transactions/{transactionId})
- create_partnerexpense: Create Partner Expense connection (POST /companies/{companyId}/sync/expenses/connections/partnerExpense)

## Fields

- `title`: string [REQUIRED for create]
- `rows`: array [REQUIRED for upsert_rows]
- `keyColumns`: array [OPTIONAL for upsert]

## Example Request Bodies

**Create Doc:**
```json
{"title": "Project Tracker"}
```

**Upsert Rows:**
```json
{"rows": [{"cells": [{"column": "Name", "value": "Task A"}, {"column": "Status", "value": "In Progress"}]}], "keyColumns": ["Name"]}
