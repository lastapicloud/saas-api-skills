---
name: klarna-payments
description: Process payments and manage orders via Klarna. Use when the user mentions
  klarna, payment, order, checkout, buy now pay later, bnpl.
version: 1.0.0
skill_type: external
base_url_env: KLARNA_BASE_URL
auth_env_var: KLARNA_API_KEY
auth_user_env: KLARNA_API_SECRET
auth_type: basic
triggers:
  - klarna
  - payment
  - order
  - checkout
  - buy now pay later
  - bnpl
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires KLARNA_BASE_URL and KLARNA_API_KEY environment variables.
---

# Klarna-Payments

Process payments and manage orders via Klarna. Use when the user mentions klarna, payment, order, checkout, buy now pay later, bnpl.

## API Endpoints

- **POST** `/payments/v1/sessions` - Create payment session
- **GET** `/payments/v1/sessions/{session_id}` - Get session
- **POST** `/payments/v1/authorizations/{authorizationToken}/order` - Create order
- **POST** `/ordermanagement/v1/orders/{order_id}/captures` - Capture order
- **POST** `/ordermanagement/v1/orders/{order_id}/refunds` - Refund order
- **GET** `/ordermanagement/v1/orders/{order_id}` - Get order
- **POST** `/ordermanagement/v1/orders/{order_id}/cancel` - Cancel order
- **DELETE** `/payments/v1/authorizations/{authorizationToken}` - Cancel an existing authorization
- **POST** `/payments/v1/authorizations/{authorizationToken}/customer-token` - Generate a consumer token
- **POST** `/payments/v1/sessions/{session_id}` - Update an existing payment session

## Actions

- create: Create payment session (POST /payments/v1/sessions)
- get_by_id: Get session (GET /payments/v1/sessions/{session_id})
- create_order: Create order (POST /payments/v1/authorizations/{authorizationToken}/order)
- create_captures: Capture order (POST /ordermanagement/v1/orders/{order_id}/captures)
- create_refunds: Refund order (POST /ordermanagement/v1/orders/{order_id}/refunds)
- get_by_id_orders: Get order (GET /ordermanagement/v1/orders/{order_id})
- create_cancel: Cancel order (POST /ordermanagement/v1/orders/{order_id}/cancel)
- delete: Cancel an existing authorization (DELETE /payments/v1/authorizations/{authorizationToken})
- create_customer_token: Generate a consumer token (POST /payments/v1/authorizations/{authorizationToken}/customer-token)
- add_sessions: Update an existing payment session (POST /payments/v1/sessions/{session_id})

## Fields

- `purchase_country`: string [REQUIRED]
- `purchase_currency`: string [REQUIRED]
- `order_amount`: integer [REQUIRED]
- `order_lines`: array [REQUIRED]

## Example Request Bodies

**Create Payment Session:**
```json
{"purchase_country": "US", "purchase_currency": "USD", "order_amount": 5000, "order_lines": [{"name": "Running Shoes", "quantity": 1, "unit_price": 5000, "total_amount": 5000}]}
```

**Capture Order:**
```json
{"captured_amount": 5000}
```
