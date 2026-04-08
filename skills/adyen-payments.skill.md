---
name: adyen-payments
description: Process payments, refunds, and manage transactions via Adyen. Use when
  the user mentions adyen, payment, checkout, refund, transaction, payout.
version: 1.0.0
skill_type: external
base_url_env: ADYEN_BASE_URL
auth_env_var: ADYEN_API_KEY
auth_type: header
triggers:
  - adyen
  - payment
  - checkout
  - refund
  - transaction
  - payout
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires ADYEN_BASE_URL and ADYEN_API_KEY environment variables.
---

# Adyen-Payments

Process payments, refunds, and manage transactions via Adyen. Use when the user mentions adyen, payment, checkout, refund, transaction, payout.

## API Endpoints

- **POST** `/v71/payments` - Create a payment
- **POST** `/v71/payments/details` - Submit payment details
- **POST** `/v71/paymentMethods` - Get available payment methods
- **POST** `/v71/payments/{paymentPspReference}/refunds` - Refund a payment
- **POST** `/v71/payments/{paymentPspReference}/captures` - Capture a payment
- **POST** `/v71/payments/{paymentPspReference}/cancels` - Cancel a payment
- **POST** `/v71/payments/{paymentPspReference}/reversals` - Reverse a payment
- **GET** `/v71/merchants/{merchantId}/paymentMethodSettings` - List payment method settings
- **POST** `/get3dsAvailability` - Check if 3D Secure is available
- **POST** `/getCostEstimate` - Get a fees cost estimate
- **POST** `/originKeys` - Create originKey values for one or more merchant domains.

## Actions

- create: Create a payment (POST /v71/payments)
- create_details: Submit payment details (POST /v71/payments/details)
- create_paymentmethods: Get available payment methods (POST /v71/paymentMethods)
- create_refunds: Refund a payment (POST /v71/payments/{paymentPspReference}/refunds)
- create_captures: Capture a payment (POST /v71/payments/{paymentPspReference}/captures)
- create_cancels: Cancel a payment (POST /v71/payments/{paymentPspReference}/cancels)
- create_reversals: Reverse a payment (POST /v71/payments/{paymentPspReference}/reversals)
- list: List payment method settings (GET /v71/merchants/{merchantId}/paymentMethodSettings)
- create_get3dsavailability: Check if 3D Secure is available (POST /get3dsAvailability)
- create_getcostestimate: Get a fees cost estimate (POST /getCostEstimate)
- create_originkeys: Create originKey values for one or more merchant domains. (POST /originKeys)

## Fields

- `amount`: object [REQUIRED for create] (value + currency)
- `reference`: string [REQUIRED for create]
- `merchantAccount`: string [REQUIRED]
- `paymentMethod`: object [REQUIRED for create]

## Example Request Bodies

**Create Payment:**
```json
{"amount": {"value": 1000, "currency": "USD"}, "reference": "order_123", "merchantAccount": "YourMerchantAccount", "paymentMethod": {"type": "scheme", "number": "4111111111111111"}}
```

**Refund Payment:**
```json
{"amount": {"value": 500, "currency": "USD"}, "merchantAccount": "YourMerchantAccount"}
