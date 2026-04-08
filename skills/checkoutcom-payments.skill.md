---
name: checkoutcom-payments
description: Manage Checkout.com payments and payouts. Use when the user mentions
  checkout.com, checkout, payment, payout.
version: 1.0.0
skill_type: external
base_url_env: CHECKOUTCOM_BASE_URL
auth_env_var: CHECKOUTCOM_SECRET_KEY
auth_type: bearer
triggers:
  - checkout.com
  - checkout
  - payment
  - payout
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires CHECKOUTCOM_BASE_URL and CHECKOUTCOM_SECRET_KEY environment
  variables.
---

# Checkoutcom-Payments

Manage Checkout.com payments and payouts. Use when the user mentions checkout.com, checkout, payment, payout.

## API Endpoints

- **POST** `/payments` - Request a payment
- **GET** `/payments/{paymentId}` - Get payment details
- **POST** `/payments/{paymentId}/captures` - Capture a payment
- **POST** `/payments/{paymentId}/voids` - Void a payment
- **POST** `/payments/{paymentId}/refunds` - Refund a payment
- **GET** `/payments` - List payments
- **POST** `/tokens` - Request a token
- **POST** `/customers` - Create a customer
- **GET** `/customers/{customerId}` - Get a customer
- **GET** `/disputes` - List disputes

## Actions

- create: Request a payment (POST /payments)
- get_by_id: Get payment details (GET /payments/{paymentId})
- create_captures: Capture a payment (POST /payments/{paymentId}/captures)
- create_voids: Void a payment (POST /payments/{paymentId}/voids)
- create_refunds: Refund a payment (POST /payments/{paymentId}/refunds)
- list: List payments (GET /payments)
- create_tokens: Request a token (POST /tokens)
- create_customers: Create a customer (POST /customers)
- get_by_id_customers: Get a customer (GET /customers/{customerId})
- list_disputes: List disputes (GET /disputes)

## Fields

- `source`: object [REQUIRED for payment] with `type`, `number`, `expiry_month`, `expiry_year`
- `amount`: integer [REQUIRED] (minor units)
- `currency`: string [REQUIRED]
- `reference`: string [OPTIONAL]

## Example Request Bodies

**Request Payment:**
```json
{"source": {"type": "card", "number": "4242424242424242", "expiry_month": 12, "expiry_year": 2026}, "amount": 5000, "currency": "USD", "reference": "order_456"}
```

**Create Customer:**
```json
{"email": "customer@example.com", "name": "Jane Doe"}
