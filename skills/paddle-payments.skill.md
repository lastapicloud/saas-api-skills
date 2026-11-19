---
name: paddle-payments
description: 'Manage products, prices, and subscriptions via Paddle. Use when the
  user mentions paddle, payment, subscription, product, price, checkout.

  '
version: 1.0.0
skill_type: external
base_url_env: PADDLE_BASE_URL
auth_env_var: PADDLE_API_KEY
auth_type: bearer
triggers:
  - paddle
  - payment
  - subscription
  - product
  - price
  - checkout
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires PADDLE_BASE_URL and PADDLE_API_KEY environment variables.
annotations:
  readOnlyHint: false
  destructiveHint: false
  idempotentHint: false
---

# Paddle-Payments

Manage products, prices, and subscriptions via Paddle. Use when the user mentions paddle, payment, subscription, product, price, checkout.


## API Endpoints

- **GET** `/products` - List products
- **POST** `/products` - Create product
- **GET** `/products/{product_id}` - Get product
- **PATCH** `/products/{product_id}` - Update product
- **GET** `/prices` - List prices
- **POST** `/prices` - Create price
- **GET** `/subscriptions` - List subscriptions
- **GET** `/subscriptions/{subscription_id}` - Get subscription

## Actions

- list: List products (GET /products)
- create: Create product (POST /products)
- get_by_id: Get product (GET /products/{product_id})
- update: Update product (PATCH /products/{product_id})
- list_prices: List prices (GET /prices)
- create_price: Create price (POST /prices)
- list_subscriptions: List subscriptions (GET /subscriptions)
- get_subscription: Get subscription (GET /subscriptions/{subscription_id})

## Fields

- `name`: string [REQUIRED for create] — Display name
- `tax_category`: string [REQUIRED for create] — Tax Category
- `description`: string [OPTIONAL] — Human-readable description

## Example Request Bodies

**Create Product:**
```json
{"name": "Pro Plan", "tax_category": "standard", "description": "Access to all premium features"}
```

**Update Product:**
```json
{"name": "Pro Plan v2", "description": "Updated premium plan with new features"}
```

## Response

**Product object:**
- `id`: string — Unique product identifier
- `name`: string — Product name or title
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
