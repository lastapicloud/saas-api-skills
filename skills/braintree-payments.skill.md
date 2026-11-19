---
name: braintree-payments
description: 'Process payments, manage customers, and handle transactions via Braintree.
  Use when the user mentions braintree, payment, transaction, customer, subscription,
  vault.

  '
version: 1.0.0
skill_type: external
base_url_env: BRAINTREE_BASE_URL
auth_env_var: BRAINTREE_PRIVATE_KEY
auth_user_env: BRAINTREE_PUBLIC_KEY
auth_type: basic
triggers:
  - braintree
  - payment
  - transaction
  - customer
  - subscription
  - vault
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires BRAINTREE_BASE_URL and BRAINTREE_PRIVATE_KEY environment variables.
annotations:
  readOnlyHint: false
  destructiveHint: true
  idempotentHint: false
---

# Braintree-Payments

Process payments, manage customers, and handle transactions via Braintree. Use when the user mentions braintree, payment, transaction, customer, subscription, vault.


## API Endpoints

- **POST** `/merchants/{merchantId}/transactions` - Create a transaction
- **GET** `/merchants/{merchantId}/transactions/{transactionId}` - Get transaction by ID
- **PUT** `/merchants/{merchantId}/transactions/{transactionId}/void` - Void a transaction
- **PUT** `/merchants/{merchantId}/transactions/{transactionId}/refund` - Refund a transaction
- **POST** `/merchants/{merchantId}/customers` - Create a customer
- **GET** `/merchants/{merchantId}/customers/{customerId}` - Get customer by ID
- **DELETE** `/merchants/{merchantId}/customers/{customerId}` - Delete a customer
- **POST** `/merchants/{merchantId}/client_token` - Generate client token

## Actions

- create: Create a transaction (POST /merchants/{merchantId}/transactions)
- get_by_id: Get transaction by ID (GET /merchants/{merchantId}/transactions/{transactionId})
- put_void: Void a transaction (PUT /merchants/{merchantId}/transactions/{transactionId}/void)
- put_refund: Refund a transaction (PUT /merchants/{merchantId}/transactions/{transactionId}/refund)
- create_customer: Create a customer (POST /merchants/{merchantId}/customers)
- get_customer_id: Get customer by ID (GET /merchants/{merchantId}/customers/{customerId})
- delete: Delete a customer (DELETE /merchants/{merchantId}/customers/{customerId})
- generate_client_token: Generate client token (POST /merchants/{merchantId}/client_token)

## Fields

- `amount`: string [REQUIRED for create] — Amount in smallest currency unit
- `payment_method_nonce`: string [REQUIRED for create] — Payment Method Nonce
- `merchantId`: string [REQUIRED] — Merchant unique identifier

## Example Request Bodies

**Create Transaction:**
```json
{"amount": "50.00", "payment_method_nonce": "fake-valid-nonce", "merchantId": "your_merchant_id"}
```

**Create Customer:**
```json
{"firstName": "John", "lastName": "Doe", "email": "john@example.com"}

## Response

**Transaction object:**
- `id`: string — Unique transaction identifier
- `name`: string — Transaction name or title
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
