---
name: wave-accounting
description: Manage invoices and customers via Wave. Use when the user mentions wave,
  accounting, invoice, customer, expense, financial.
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
- create_graphql: Create invoice (mutation) (POST /graphql)
- create_graphql_2: List invoices (query) (POST /graphql)
- create_graphql_3: Create customer (mutation) (POST /graphql)
- create_graphql_4: List customers (query) (POST /graphql)
- create_graphql_5: List businesses (query) (POST /graphql)

## Fields

- `query`: string [REQUIRED] (GraphQL query/mutation)
- `variables`: object [OPTIONAL]

## Example Request Bodies

**Create Invoice (GraphQL):**
```json
{"query": "mutation { invoiceCreate(input: { businessId: \"BIZ123\", customerId: \"CUST456\", items: [{ description: \"Consulting\", unitPrice: 150.00, quantity: 2 }] }) { invoice { id } } }"}
```

**Create Customer (GraphQL):**
```json
{"query": "mutation { customerCreate(input: { businessId: \"BIZ123\", name: \"Acme Corp\", email: \"billing@acme.com\" }) { customer { id } } }"}
