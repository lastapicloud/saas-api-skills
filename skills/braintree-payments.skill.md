---
name: braintree-payments
description: Process payments, manage customers, and handle transactions via Braintree.
  Use when the user mentions braintree, payment, transaction, customer, subscription,
  vault.
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
- create_customers: Create a customer (POST /merchants/{merchantId}/customers)
- get_by_id_customers: Get customer by ID (GET /merchants/{merchantId}/customers/{customerId})
- delete: Delete a customer (DELETE /merchants/{merchantId}/customers/{customerId})
- create_client_token: Generate client token (POST /merchants/{merchantId}/client_token)

## Fields

- `amount`: string [REQUIRED for create]
- `payment_method_nonce`: string [REQUIRED for create]
- `merchantId`: string [REQUIRED]

## Example Request Bodies

**Create Transaction:**
```json
{"amount": "50.00", "payment_method_nonce": "fake-valid-nonce", "merchantId": "your_merchant_id"}
```

**Create Customer:**
```json
{"firstName": "John", "lastName": "Doe", "email": "john@example.com"}
