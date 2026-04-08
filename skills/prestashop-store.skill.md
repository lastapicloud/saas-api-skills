---
name: prestashop-store
description: Manage products and orders via PrestaShop. Use when the user mentions
  prestashop, product, order, customer, store, ecommerce.
version: 1.0.0
skill_type: external
base_url_env: PRESTASHOP_BASE_URL
auth_env_var: PRESTASHOP_API_KEY
auth_type: basic
triggers:
  - prestashop
  - product
  - order
  - customer
  - store
  - ecommerce
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires PRESTASHOP_BASE_URL and PRESTASHOP_API_KEY environment variables.
---

# Prestashop-Store

Manage products and orders via PrestaShop. Use when the user mentions prestashop, product, order, customer, store, ecommerce.

## API Endpoints

- **GET** `/api/products` - List products
- **POST** `/api/products` - Create product
- **GET** `/api/products/{id}` - Get product
- **PUT** `/api/products/{id}` - Update product
- **DELETE** `/api/products/{id}` - Delete product
- **GET** `/api/orders` - List orders
- **GET** `/api/customers` - List customers
- **GET** `/api/categories` - List categories

## Actions

- list: List products (GET /api/products)
- create: Create product (POST /api/products)
- get_by_id: Get product (GET /api/products/{id})
- update: Update product (PUT /api/products/{id})
- delete: Delete product (DELETE /api/products/{id})
- list_orders: List orders (GET /api/orders)
- list_customers: List customers (GET /api/customers)
- list_categories: List categories (GET /api/categories)

## Fields

- `name`: string [REQUIRED for create]
- `price`: number [REQUIRED for create]

## Example Request Bodies

**Create Product:**
```json
{"name": "Wireless Keyboard", "price": 49.99}
```

**Update Product:**
```json
{"name": "Wireless Keyboard Pro", "price": 59.99}
```
