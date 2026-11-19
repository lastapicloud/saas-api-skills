---
name: paypal-payments
description: 'Manage payments, orders, payouts, and subscriptions in PayPal. Use when
  the user mentions paypal, payment, payout, order, subscription, billing.

  '
version: 1.0.0
skill_type: external
base_url_env: PAYPAL_BASE_URL
auth_env_var: PAYPAL_ACCESS_TOKEN
auth_type: bearer
triggers:
  - paypal
  - payment
  - payout
  - order
  - subscription
  - billing
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires PAYPAL_BASE_URL and PAYPAL_ACCESS_TOKEN environment variables.
annotations:
  readOnlyHint: false
  destructiveHint: false
  idempotentHint: false
---

# Paypal-Payments

Manage payments, orders, payouts, and subscriptions in PayPal. Use when the user mentions paypal, payment, payout, order, subscription, billing.


## API Endpoints

- **POST** `/v2/checkout/orders` - Create an order
- **GET** `/v2/checkout/orders/{order_id}` - Get order details
- **POST** `/v2/checkout/orders/{order_id}/capture` - Capture an order
- **GET** `/v2/payments/captures/{capture_id}` - Get capture details
- **POST** `/v2/payments/captures/{capture_id}/refund` - Refund a capture
- **POST** `/v1/payments/payouts` - Create a payout
- **GET** `/v1/billing/subscriptions/{subscription_id}` - Get subscription details
- **POST** `/v1/billing/plans` - Create a billing plan
- **POST** `/v2/checkout/orders/order-update-callback` - Receive updated order information via callback URL
- **PATCH** `/v2/checkout/orders/{id}` - Update order
- **GET** `/v2/checkout/orders/{id}` - Show order details
- **POST** `/v2/checkout/orders/{id}/confirm-payment-source` - Confirm the Order
- **POST** `/v2/checkout/orders/{id}/authorize` - Authorize payment for order
- **POST** `/v2/checkout/orders/{id}/capture` - Capture payment for order
- **POST** `/v2/checkout/orders/{id}/track` - Add tracking information for an Order.

## Actions

- create: Create an order (POST /v2/checkout/orders)
- get_by_id: Get order details (GET /v2/checkout/orders/{order_id})
- capture_order: Capture an order (POST /v2/checkout/orders/{order_id}/capture)
- get_capture_details: Get capture details (GET /v2/payments/captures/{capture_id})
- refund_capture: Refund a capture (POST /v2/payments/captures/{capture_id}/refund)
- create_payout: Create a payout (POST /v1/payments/payouts)
- get_subscription_details: Get subscription details (GET /v1/billing/subscriptions/{subscription_id})
- create_billing_plan: Create a billing plan (POST /v1/billing/plans)
- create_receive_updated_order_information: Receive updated order information via callback URL (POST /v2/checkout/orders/order-update-callback)
- update: Update order (PATCH /v2/checkout/orders/{id})
- get_show_order_details: Show order details (GET /v2/checkout/orders/{id})
- create_confirm_order: Confirm the Order (POST /v2/checkout/orders/{id}/confirm-payment-source)
- create_authorize_payment_order: Authorize payment for order (POST /v2/checkout/orders/{id}/authorize)
- capture_payment_order: Capture payment for order (POST /v2/checkout/orders/{id}/capture)
- add_tracking_information_order: Add tracking information for an Order. (POST /v2/checkout/orders/{id}/track)

## Fields

- `order_id`: string [REQUIRED for get_order, capture_order] (order ID) — Order unique identifier
- `capture_id`: string [REQUIRED for get_capture, refund_capture] (capture ID) — Capture unique identifier
- `subscription_id`: string [REQUIRED for get_subscription] (subscription ID) — Subscription unique identifier
- `intent`: string [REQUIRED for create_order] (CAPTURE or AUTHORIZE) — Intent
- `purchase_units`: array [REQUIRED for create_order] (list of purchase unit objects) — List of purchase units
- `amount`: object [REQUIRED in purchase_units] (currency_code and value) — Amount in smallest currency unit
- `note_to_payer`: string [OPTIONAL for refund_capture] (refund reason) — Note To Payer

## Example Request Bodies

**Create Order:**
```json
{"intent": "CAPTURE", "purchase_units": [{"amount": {"currency_code": "USD", "value": "50.00"}}]}
```

**Refund Capture:**
```json
{"amount": {"currency_code": "USD", "value": "10.00"}, "note_to_payer": "Partial refund"}
```

**Create Payout:**
```json
{"sender_batch_header": {"sender_batch_id": "batch_001", "email_subject": "You have a payout!"}, "items": [{"recipient_type": "EMAIL", "amount": {"value": "25.00", "currency": "USD"}, "receiver": "user@example.com"}]}
```

## Response

**Order object:**
- `id`: string — Unique order identifier
- `name`: string — Order name or title
- `status`: string — Current status
- `created_at`: string — Creation timestamp (ISO 8601)
- `updated_at`: string — Last update timestamp (ISO 8601)


**Required fields reference:**
```json
{
  "order_id": "example_order_id",
  "capture_id": "example_capture_id",
  "subscription_id": "example_subscription_id"
}
```


**Required fields reference:**
```json
{
  "order_id": "example_order_id",
  "capture_id": "example_capture_id",
  "subscription_id": "example_subscription_id"
}
```

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
