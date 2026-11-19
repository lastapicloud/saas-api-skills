---
name: wave-accounting
description: 'Manage invoices and customers via Wave. Use when the user mentions wave,
  accounting, invoice, customer, expense, financial.

  '
version: 1.0.0
skill_type: external
base_url_env: WAVE_BASE_URL
auth_env_var: WAVE_ACCESS_TOKEN
auth_type: bearer
triggers:
  - wave
  - accounting
  - invoice
  - customer
  - expense
  - financial
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires WAVE_BASE_URL and WAVE_ACCESS_TOKEN environment variables.
annotations:
  readOnlyHint: false
  destructiveHint: false
  idempotentHint: false
---

# Wave-Accounting

Manage invoices and customers via Wave. Use when the user mentions wave, accounting, invoice, customer, expense, financial.


## API Endpoints

- **POST** `/graphql` - GraphQL query
- **POST** `/graphql` - Create invoice (mutation)
- **POST** `/graphql` - List invoices (query)
- **POST** `/graphql` - Create customer (mutation)
- **POST** `/graphql` - List customers (query)
- **POST** `/graphql` - List businesses (query)

## Actions

- create: GraphQL query (POST /graphql)
- create_invoice_mutation: Create invoice (mutation) (POST /graphql)
- list_invoices_query: List invoices (query) (POST /graphql)
- create_customer_mutation: Create customer (mutation) (POST /graphql)
- list_customers_query: List customers (query) (POST /graphql)
- list_businesses_query: List businesses (query) (POST /graphql)

## Fields

- `query`: string [REQUIRED] (GraphQL query/mutation) — Search or filter query
- `variables`: object [OPTIONAL] — Variables configuration

## Example Request Bodies

**Create Invoice (GraphQL):**
```json
{"query": "mutation { invoiceCreate(input: { businessId: \"BIZ123\", customerId: \"CUST456\", items: [{ description: \"Consulting\", unitPrice: 150.00, quantity: 2 }] }) { invoice { id } } }"}
```

**Create Customer (GraphQL):**
```json
{"query": "mutation { customerCreate(input: { businessId: \"BIZ123\", name: \"Acme Corp\", email: \"billing@acme.com\" }) { customer { id } } }"}

## Response

**Graphql object:**
- `id`: string — Unique graphql identifier
- `name`: string — Graphql name or title
- `status`: string — Current status
- `created_at`: string — Creation timestamp (ISO 8601)
- `updated_at`: string — Last update timestamp (ISO 8601)

## Error Responses

| Status | Meaning |
|--------|---------|
| 400 | Invalid request body — check required fields and types |
| 401 | Authentication failed — verify API key or token is valid and not expired |
| 403 | Forbidden — insufficient permissions or scope for this action |
| 409 | Conflict — resource already exists or concurrent modification |
| 429 | Rate limited — too many requests, retry after delay |
| 500 | Server error — retry or check service status page |
