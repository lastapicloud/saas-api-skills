---
name: paddle-payments
description: Manage products, prices, and subscriptions via Paddle. Use when the user
  mentions paddle, payment, subscription, product, price, checkout.
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
- create_prices: Create price (POST /prices)
- list_subscriptions: List subscriptions (GET /subscriptions)
- get_by_id_subscriptions: Get subscription (GET /subscriptions/{subscription_id})

## Fields

- `name`: string [REQUIRED for create]
- `tax_category`: string [REQUIRED for create]
- `description`: string [OPTIONAL]

## Example Request Bodies

**Create Product:**
```json
{"name": "Pro Plan", "tax_category": "standard", "description": "Access to all premium features"}
```

**Update Product:**
```json
{"name": "Pro Plan v2", "description": "Updated premium plan with new features"}
```
