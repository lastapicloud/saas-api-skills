---
name: worldpay-payments
description: Process payments and manage transactions via Worldpay. Use when the user
  mentions worldpay, payment, transaction, card, refund, 3ds.
version: 1.0.0
skill_type: external
base_url_env: WORLDPAY_BASE_URL
auth_env_var: WORLDPAY_API_KEY
auth_type: header
triggers:
  - worldpay
  - payment
  - transaction
  - card
  - refund
  - 3ds
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires WORLDPAY_BASE_URL and WORLDPAY_API_KEY environment variables.
---

# Worldpay-Payments

Process payments and manage transactions via Worldpay. Use when the user mentions worldpay, payment, transaction, card, refund, 3ds.

## API Endpoints

- **POST** `/payments` - Create payment
- **GET** `/payments/{paymentId}` - Get payment
- **POST** `/payments/{paymentId}/refunds` - Refund payment
- **POST** `/payments/{paymentId}/cancellations` - Cancel payment
- **POST** `/payments/{paymentId}/partialRefunds` - Partial refund
- **GET** `/payments` - Query payments
- **POST** `/tokens` - Create token

## Actions

- create: Create payment (POST /payments)
- get_by_id: Get payment (GET /payments/{paymentId})
- create_refunds: Refund payment (POST /payments/{paymentId}/refunds)
- create_cancellations: Cancel payment (POST /payments/{paymentId}/cancellations)
- create_partialrefunds: Partial refund (POST /payments/{paymentId}/partialRefunds)
- list: Query payments (GET /payments)
- create_tokens: Create token (POST /tokens)

## Fields

- `paymentInstrument`: object [REQUIRED for create]
- `merchant`: object [REQUIRED for create]
- `instruction`: object [REQUIRED for create]

## Example Request Bodies

**Create Payment:**
```json
{"paymentInstrument": {"type": "card/plain", "cardNumber": "4444333322221111", "expiryDate": {"month": 12, "year": 2028}}, "merchant": {"entity": "default"}, "instruction": {"value": {"amount": 2500, "currency": "GBP"}}}
```

**Create Token:**
```json
{"paymentInstrument": {"type": "card/plain", "cardNumber": "4444333322221111", "expiryDate": {"month": 12, "year": 2028}}}
```
