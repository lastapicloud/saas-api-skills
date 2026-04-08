---
name: quickbooks-accounting
description: Manage QuickBooks invoices, customers, and accounts. Use when the user
  mentions quickbooks, invoice, customer, accounting, payment, expense.
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
- create_invoice: Update an invoice (POST /v3/company/{companyId}/invoice)
- delete: Delete an invoice (DELETE /v3/company/{companyId}/invoice/{invoiceId})
- get_by_id_customer: Get a customer (GET /v3/company/{companyId}/customer/{customerId})
- create_customer: Create a customer (POST /v3/company/{companyId}/customer)
- list: Profit & Loss report (GET /v3/company/{companyId}/reports/ProfitAndLoss)
- create_payment: Create a payment (POST /v3/company/{companyId}/payment)
- get_by_id_companyinfo: Get company info (GET /v3/company/{companyId}/companyinfo/{companyId})

## Fields

- `CustomerRef`: object [REQUIRED for invoice] with `value` (customer ID)
- `Line`: array [REQUIRED for invoice] with `Amount`, `DetailType`, `SalesItemLineDetail`
- `DisplayName`: string [REQUIRED for customer]
- `PrimaryEmailAddr`: object [OPTIONAL] with `Address`
- `query`: string [REQUIRED for query] (e.g., "SELECT * FROM Invoice")

## Example Request Bodies

**Create Invoice:**
```json
{"CustomerRef": {"value": "12"}, "Line": [{"Amount": 150.00, "DetailType": "SalesItemLineDetail", "SalesItemLineDetail": {"ItemRef": {"value": "1"}}}]}
```

**Create Customer:**
```json
{"DisplayName": "Acme Corp", "PrimaryEmailAddr": {"Address": "billing@acme.com"}}
