---
name: square-payments
description: Manage Square payments, orders, and customers. Use when the user mentions
  square, payment, order, customer, catalog.
version: 1.0.0
skill_type: external
base_url_env: SQUARE_BASE_URL
auth_env_var: SQUARE_ACCESS_TOKEN
auth_type: bearer
triggers:
  - square
  - payment
  - order
  - customer
  - catalog
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires SQUARE_BASE_URL and SQUARE_ACCESS_TOKEN environment variables.
---

# Square-Payments

Manage Square payments, orders, and customers. Use when the user mentions square, payment, order, customer, catalog.

## API Endpoints

- **POST** `/v2/payments` - Create a payment
- **GET** `/v2/payments` - List payments
- **GET** `/v2/payments/{paymentId}` - Get a payment
- **POST** `/v2/refunds` - Create a refund
- **POST** `/v2/orders` - Create an order
- **GET** `/v2/customers` - List customers
- **POST** `/v2/customers` - Create a customer
- **GET** `/v2/catalog/list` - List catalog items
- **POST** `/v2/catalog/object` - Create a catalog object
- **GET** `/v2/locations` - List locations
- **POST** `/v2/invoices/search` - SearchInvoices
- **GET** `/v2/invoices` - ListInvoices
- **PUT** `/v2/invoices/{invoice_id}` - UpdateInvoice
- **DELETE** `/v2/invoices/{invoice_id}` - DeleteInvoice
- **POST** `/v2/customers/search` - SearchCustomers

## Actions

- create: Create a payment (POST /v2/payments)
- list: List payments (GET /v2/payments)
- get_by_id: Get a payment (GET /v2/payments/{paymentId})
- create_refunds: Create a refund (POST /v2/refunds)
- create_orders: Create an order (POST /v2/orders)
- list_customers: List customers (GET /v2/customers)
- create_customers: Create a customer (POST /v2/customers)
- list_catalog: List catalog items (GET /v2/catalog/list)
- create_object: Create a catalog object (POST /v2/catalog/object)
- list_locations: List locations (GET /v2/locations)
- search: SearchInvoices (POST /v2/invoices/search)
- list_invoices: ListInvoices (GET /v2/invoices)
- update: UpdateInvoice (PUT /v2/invoices/{invoice_id})
- delete: DeleteInvoice (DELETE /v2/invoices/{invoice_id})
- search_customers: SearchCustomers (POST /v2/customers/search)

## Fields

- `source_id`: string [REQUIRED for payment] (nonce or token)
- `amount_money`: object [REQUIRED] with `amount` (integer, cents) and `currency`
- `idempotency_key`: string [REQUIRED]
- `location_id`: string [REQUIRED for order]
- `given_name`: string [OPTIONAL for customer]
- `email_address`: string [OPTIONAL for customer]

## Example Request Bodies

**Create Payment:**
```json
{"source_id": "cnon:card-nonce-ok", "amount_money": {"amount": 1500, "currency": "USD"}, "idempotency_key": "unique-key-123"}
```

**Create Customer:**
```json
{"given_name": "Jane", "email_address": "jane@example.com", "idempotency_key": "cust-key-456"}
```
