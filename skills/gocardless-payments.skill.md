---
name: gocardless-payments
description: Manage direct debit payments via GoCardless. Use when the user mentions
  gocardless, direct debit, payment, mandate, customer, subscription.
version: 1.0.0
skill_type: external
base_url_env: GOCARDLESS_BASE_URL
auth_env_var: GOCARDLESS_ACCESS_TOKEN
auth_type: bearer
triggers:
  - gocardless
  - direct debit
  - payment
  - mandate
  - customer
  - subscription
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires GOCARDLESS_BASE_URL and GOCARDLESS_ACCESS_TOKEN environment
  variables.
---

# Gocardless-Payments

Manage direct debit payments via GoCardless. Use when the user mentions gocardless, direct debit, payment, mandate, customer, subscription.

## API Endpoints

- **GET** `/customers` - List customers
- **POST** `/customers` - Create customer
- **GET** `/customers/{id}` - Get customer
- **GET** `/mandates` - List mandates
- **POST** `/mandates` - Create mandate
- **GET** `/payments` - List payments
- **POST** `/payments` - Create payment
- **GET** `/subscriptions` - List subscriptions

## Actions

- list: List customers (GET /customers)
- create: Create customer (POST /customers)
- get_by_id: Get customer (GET /customers/{id})
- list_mandates: List mandates (GET /mandates)
- create_mandates: Create mandate (POST /mandates)
- list_payments: List payments (GET /payments)
- create_payments: Create payment (POST /payments)
- list_subscriptions: List subscriptions (GET /subscriptions)

## Fields

- `amount`: integer [REQUIRED for create] (in pence/cents)
- `currency`: string [REQUIRED for create]
- `mandate`: string [REQUIRED for create] (mandate ID)
- `email`: string [REQUIRED for create_customer]

## Example Request Bodies

**Create Customer:**
```json
{"email": "customer@example.com", "metadata": {"account_id": "ACC-001"}}
```

**Create Payment:**
```json
{"amount": 5000, "currency": "GBP", "mandate": "MD000123"}
