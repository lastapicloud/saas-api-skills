---
name: mollie-payments
description: Process payments and manage orders via Mollie. Use when the user mentions
  mollie, payment, order, refund, subscription, checkout.
version: 1.0.0
skill_type: external
base_url_env: MOLLIE_BASE_URL
auth_env_var: MOLLIE_API_KEY
auth_type: bearer
triggers:
  - mollie
  - payment
  - order
  - refund
  - subscription
  - checkout
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires MOLLIE_BASE_URL and MOLLIE_API_KEY environment variables.
---

# Mollie-Payments

Process payments and manage orders via Mollie. Use when the user mentions mollie, payment, order, refund, subscription, checkout.

## API Endpoints

- **POST** `/v2/payments` - Create payment
- **GET** `/v2/payments` - List payments
- **GET** `/v2/payments/{id}` - Get payment
- **DELETE** `/v2/payments/{id}` - Cancel payment
- **POST** `/v2/payments/{id}/refunds` - Create refund
- **GET** `/v2/customers` - List customers
- **POST** `/v2/customers` - Create customer
- **GET** `/v2/methods` - List payment methods

## Actions

- create: Create payment (POST /v2/payments)
- list: List payments (GET /v2/payments)
- get_by_id: Get payment (GET /v2/payments/{id})
- delete: Cancel payment (DELETE /v2/payments/{id})
- create_refunds: Create refund (POST /v2/payments/{id}/refunds)
- list_customers: List customers (GET /v2/customers)
- create_customers: Create customer (POST /v2/customers)
- list_methods: List payment methods (GET /v2/methods)

## Fields

- `amount`: object [REQUIRED for create] (value, currency)
- `description`: string [REQUIRED for create]
- `redirectUrl`: string [REQUIRED for create]

## Example Request Bodies

**Create Payment:**
```json
{"amount": {"value": "25.00", "currency": "EUR"}, "description": "Order #12345", "redirectUrl": "https://example.com/payment/complete"}
```

**Create Customer:**
```json
{"name": "John Doe", "email": "john@example.com"}
```
