---
name: quickbooks-accounting
description: 'Manage QuickBooks invoices, customers, and accounts. Use when the user
  mentions quickbooks, invoice, customer, accounting, payment, expense.

  '
version: 1.0.0
skill_type: external
base_url_env: QUICKBOOKS_BASE_URL
auth_env_var: QUICKBOOKS_ACCESS_TOKEN
auth_type: bearer
triggers:
  - quickbooks
  - invoice
  - customer
  - accounting
  - payment
  - expense
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires QUICKBOOKS_BASE_URL and QUICKBOOKS_ACCESS_TOKEN environment
  variables.
annotations:
  readOnlyHint: false
  destructiveHint: true
  idempotentHint: false
---

# Quickbooks-Accounting

Manage QuickBooks invoices, customers, and accounts. Use when the user mentions quickbooks, invoice, customer, accounting, payment, expense.


## API Endpoints

- **GET** `/v3/company/{companyId}/query` - Query entities (SQL-like)
- **GET** `/v3/company/{companyId}/invoice/{invoiceId}` - Get an invoice
- **POST** `/v3/company/{companyId}/invoice` - Create an invoice
- **POST** `/v3/company/{companyId}/invoice` - Update an invoice
- **DELETE** `/v3/company/{companyId}/invoice/{invoiceId}` - Delete an invoice
- **GET** `/v3/company/{companyId}/customer/{customerId}` - Get a customer
- **POST** `/v3/company/{companyId}/customer` - Create a customer
- **GET** `/v3/company/{companyId}/reports/ProfitAndLoss` - Profit & Loss report
- **POST** `/v3/company/{companyId}/payment` - Create a payment
- **GET** `/v3/company/{companyId}/companyinfo/{companyId}` - Get company info

## Actions

- query: Query entities (SQL-like) (GET /v3/company/{companyId}/query)
- get_by_id: Get an invoice (GET /v3/company/{companyId}/invoice/{invoiceId})
- create: Create an invoice (POST /v3/company/{companyId}/invoice)
- update_invoice: Update an invoice (POST /v3/company/{companyId}/invoice)
- delete: Delete an invoice (DELETE /v3/company/{companyId}/invoice/{invoiceId})
- get_customer: Get a customer (GET /v3/company/{companyId}/customer/{customerId})
- create_customer: Create a customer (POST /v3/company/{companyId}/customer)
- list: Profit & Loss report (GET /v3/company/{companyId}/reports/ProfitAndLoss)
- create_payment: Create a payment (POST /v3/company/{companyId}/payment)
- get_company_info: Get company info (GET /v3/company/{companyId}/companyinfo/{companyId})

## Fields

- `CustomerRef`: object [REQUIRED for invoice] with `value` (customer ID) — Customerref configuration
- `Line`: array [REQUIRED for invoice] with `Amount`, `DetailType`, `SalesItemLineDetail` — List of Line
- `DisplayName`: string [REQUIRED for customer] — Display display name
- `PrimaryEmailAddr`: object [OPTIONAL] with `Address` — Primaryemailaddr configuration
- `query`: string [REQUIRED for query] (e.g., "SELECT * FROM Invoice") — Search or filter query

## Example Request Bodies

**Create Invoice:**
```json
{"CustomerRef": {"value": "12"}, "Line": [{"Amount": 150.00, "DetailType": "SalesItemLineDetail", "SalesItemLineDetail": {"ItemRef": {"value": "1"}}}]}
```

**Create Customer:**
```json
{"DisplayName": "Acme Corp", "PrimaryEmailAddr": {"Address": "billing@acme.com"}}

## Response

**Invoice object:**
- `id`: string — Unique invoice identifier
- `name`: string — Invoice name or title
- `status`: string — Current status
- `created_at`: string — Creation timestamp (ISO 8601)
- `updated_at`: string — Last update timestamp (ISO 8601)

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
