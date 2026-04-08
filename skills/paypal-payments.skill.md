---
name: paypal-payments
description: Manage payments, orders, payouts, and subscriptions in PayPal. Use when
  the user mentions paypal, payment, payout, order, subscription, billing.
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
- create_capture: Capture an order (POST /v2/checkout/orders/{order_id}/capture)
- get_by_id_captures: Get capture details (GET /v2/payments/captures/{capture_id})
- create_refund: Refund a capture (POST /v2/payments/captures/{capture_id}/refund)
- create_payouts: Create a payout (POST /v1/payments/payouts)
- get_by_id_subscriptions: Get subscription details (GET /v1/billing/subscriptions/{subscription_id})
- create_plans: Create a billing plan (POST /v1/billing/plans)
- create_order_update_callback: Receive updated order information via callback URL (POST /v2/checkout/orders/order-update-callback)
- update: Update order (PATCH /v2/checkout/orders/{id})
- get_by_id_orders: Show order details (GET /v2/checkout/orders/{id})
- create_confirm_payment_source: Confirm the Order (POST /v2/checkout/orders/{id}/confirm-payment-source)
- create_authorize: Authorize payment for order (POST /v2/checkout/orders/{id}/authorize)
- create_capture_2: Capture payment for order (POST /v2/checkout/orders/{id}/capture)
- create_track: Add tracking information for an Order. (POST /v2/checkout/orders/{id}/track)

## Fields

- `order_id`: string [REQUIRED for get_order, capture_order] (order ID)
- `capture_id`: string [REQUIRED for get_capture, refund_capture] (capture ID)
- `subscription_id`: string [REQUIRED for get_subscription] (subscription ID)
- `intent`: string [REQUIRED for create_order] (CAPTURE or AUTHORIZE)
- `purchase_units`: array [REQUIRED for create_order] (list of purchase unit objects)
- `amount`: object [REQUIRED in purchase_units] (currency_code and value)
- `note_to_payer`: string [OPTIONAL for refund_capture] (refund reason)

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
