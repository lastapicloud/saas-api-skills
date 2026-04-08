---
name: netsuite-erp
description: Manage records and transactions via NetSuite. Use when the user mentions
  netsuite, erp, invoice, customer, vendor, sales order, purchase order.
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
- list_invoice: List invoices (GET /record/v1/invoice)
- create_invoice: Create invoice (POST /record/v1/invoice)
- list_salesorder: List sales orders (GET /record/v1/salesOrder)

## Fields

- `companyName`: string [REQUIRED for create]
- `email`: string [OPTIONAL]
- `subsidiary`: object [OPTIONAL]

## Example Request Bodies

**Create Customer:**
```json
{"companyName": "Acme Corp", "email": "accounts@acme.com", "subsidiary": {"id": "1"}}
```

**Create Invoice:**
```json
{"entity": {"id": "123"}, "item": {"items": [{"item": {"id": "456"}, "quantity": 2, "rate": 50.00}]}}
```
