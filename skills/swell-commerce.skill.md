---
name: swell-commerce
description: Manage products, orders, and accounts via Swell. Use when the user mentions
  swell, product, order, account, ecommerce, headless commerce.
version: 1.0.0
skill_type: external
base_url_env: SWELL_BASE_URL
auth_env_var: SWELL_SECRET_KEY
auth_user_env: SWELL_STORE_ID
auth_type: basic
triggers:
  - swell
  - product
  - order
  - account
  - ecommerce
  - headless commerce
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires SWELL_BASE_URL and SWELL_SECRET_KEY environment variables.
---

# Swell-Commerce

Manage products, orders, and accounts via Swell. Use when the user mentions swell, product, order, account, ecommerce, headless commerce.

## API Endpoints

- **GET** `/:products` - List products
- **POST** `/:products` - Create product
- **GET** `/:products/{id}` - Get product
- **PUT** `/:products/{id}` - Update product
- **DELETE** `/:products/{id}` - Delete product
- **GET** `/:orders` - List orders
- **GET** `/:accounts` - List accounts
- **GET** `/:categories` - List categories

## Actions

- list: List products (GET /:products)
- create: Create product (POST /:products)
- get_by_id: Get product (GET /:products/{id})
- update: Update product (PUT /:products/{id})
- delete: Delete product (DELETE /:products/{id})
- list_orders: List orders (GET /:orders)
- list_accounts: List accounts (GET /:accounts)
- list_categories: List categories (GET /:categories)

## Fields

- `name`: string [REQUIRED for create]
- `price`: number [OPTIONAL]
- `active`: boolean [OPTIONAL]

## Example Request Bodies

**Create Product:**
```json
{"name": "Premium T-Shirt", "price": 29.99, "active": true}
```

**Update Product:**
```json
{"name": "Premium T-Shirt V2", "price": 34.99}
```
