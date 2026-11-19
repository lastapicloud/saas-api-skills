---
name: netsuite-erp
description: 'Manage records and transactions via NetSuite. Use when the user mentions
  netsuite, erp, invoice, customer, vendor, sales order, purchase order.

  '
version: 1.0.0
skill_type: external
base_url_env: NETSUITE_BASE_URL
auth_env_var: NETSUITE_ACCESS_TOKEN
auth_type: bearer
triggers:
  - netsuite
  - erp
  - invoice
  - customer
  - vendor
  - sales order
  - purchase order
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires NETSUITE_BASE_URL and NETSUITE_ACCESS_TOKEN environment variables.
annotations:
  readOnlyHint: false
  destructiveHint: true
  idempotentHint: false
---

# Netsuite-Erp

Manage records and transactions via NetSuite. Use when the user mentions netsuite, erp, invoice, customer, vendor, sales order, purchase order.


## API Endpoints

- **GET** `/record/v1/customer` - List customers
- **POST** `/record/v1/customer` - Create customer
- **GET** `/record/v1/customer/{id}` - Get customer
- **PATCH** `/record/v1/customer/{id}` - Update customer
- **DELETE** `/record/v1/customer/{id}` - Delete customer
- **GET** `/record/v1/invoice` - List invoices
- **POST** `/record/v1/invoice` - Create invoice
- **GET** `/record/v1/salesOrder` - List sales orders

## Actions

- list: List customers (GET /record/v1/customer)
- create: Create customer (POST /record/v1/customer)
- get_by_id: Get customer (GET /record/v1/customer/{id})
- update: Update customer (PATCH /record/v1/customer/{id})
- delete: Delete customer (DELETE /record/v1/customer/{id})
- list_invoices: List invoices (GET /record/v1/invoice)
- create_invoice: Create invoice (POST /record/v1/invoice)
- list_sales_orders: List sales orders (GET /record/v1/salesOrder)

## Fields

- `companyName`: string [REQUIRED for create] — Company display name
- `email`: string [OPTIONAL] — Email address
- `subsidiary`: object [OPTIONAL] — Subsidiary configuration

## Example Request Bodies

**Create Customer:**
```json
{"companyName": "Acme Corp", "email": "accounts@acme.com", "subsidiary": {"id": "1"}}
```

**Create Invoice:**
```json
{"entity": {"id": "123"}, "item": {"items": [{"item": {"id": "456"}, "quantity": 2, "rate": 50.00}]}}
```

## Response

**Customer object:**
- `id`: string — Unique customer identifier
- `name`: string — Customer name or title
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
