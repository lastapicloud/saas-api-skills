---
name: lemonsqueezy-payments
description: Manage Lemon Squeezy products, orders, and subscriptions. Use when the
  user mentions lemon squeezy, lemonsqueezy, product, order, subscription, checkout.
version: 1.0.0
skill_type: external
base_url_env: LEMONSQUEEZY_BASE_URL
auth_env_var: LEMONSQUEEZY_API_KEY
auth_type: bearer
triggers:
  - lemon squeezy
  - lemonsqueezy
  - product
  - order
  - subscription
  - checkout
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires LEMONSQUEEZY_BASE_URL and LEMONSQUEEZY_API_KEY environment
  variables.
---

# Lemonsqueezy-Payments

Manage Lemon Squeezy products, orders, and subscriptions. Use when the user mentions lemon squeezy, lemonsqueezy, product, order, subscription, checkout.

## API Endpoints

- **GET** `/v1/products` - List products
- **GET** `/v1/products/{productId}` - Get a product
- **GET** `/v1/orders` - List orders
- **GET** `/v1/orders/{orderId}` - Get an order
- **GET** `/v1/subscriptions` - List subscriptions
- **GET** `/v1/subscriptions/{subscriptionId}` - Get a subscription
- **PATCH** `/v1/subscriptions/{subscriptionId}` - Update a subscription
- **DELETE** `/v1/subscriptions/{subscriptionId}` - Cancel a subscription
- **GET** `/v1/stores` - List stores
- **GET** `/v1/customers` - List customers

## Actions

- list: List products (GET /v1/products)
- get_by_id: Get a product (GET /v1/products/{productId})
- list_orders: List orders (GET /v1/orders)
- get_by_id_orders: Get an order (GET /v1/orders/{orderId})
- list_subscriptions: List subscriptions (GET /v1/subscriptions)
- get_by_id_subscriptions: Get a subscription (GET /v1/subscriptions/{subscriptionId})
- update: Update a subscription (PATCH /v1/subscriptions/{subscriptionId})
- delete: Cancel a subscription (DELETE /v1/subscriptions/{subscriptionId})
- list_stores: List stores (GET /v1/stores)
- list_customers: List customers (GET /v1/customers)

## Fields

- `data`: object [REQUIRED for update] with `type`, `id`, `attributes`
- `cancelled`: boolean [OPTIONAL for update subscription]

## Example Request Bodies

**Update Subscription:**
```json
{"data": {"type": "subscriptions", "id": "sub_12345", "attributes": {"cancelled": false}}}
```

**Cancel Subscription:**
```json
{"data": {"type": "subscriptions", "id": "sub_12345", "attributes": {"cancelled": true}}}
```
