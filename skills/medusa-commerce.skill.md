---
name: medusa-commerce
description: Manage products and orders via Medusa e-commerce. Use when the user mentions
  medusa, product, order, customer, cart, ecommerce, headless commerce.
version: 1.0.0
skill_type: external
base_url_env: MEDUSA_BASE_URL
auth_env_var: MEDUSA_API_TOKEN
auth_type: bearer
triggers:
  - medusa
  - product
  - order
  - customer
  - cart
  - ecommerce
  - headless commerce
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires MEDUSA_BASE_URL and MEDUSA_API_TOKEN environment variables.
---

# Medusa-Commerce

Manage products and orders via Medusa e-commerce. Use when the user mentions medusa, product, order, customer, cart, ecommerce, headless commerce.

## API Endpoints

- **GET** `/admin/products` - List products
- **POST** `/admin/products` - Create product
- **GET** `/admin/products/{id}` - Get product
- **POST** `/admin/products/{id}` - Update product
- **DELETE** `/admin/products/{id}` - Delete product
- **GET** `/admin/orders` - List orders
- **GET** `/admin/customers` - List customers
- **GET** `/admin/regions` - List regions

## Actions

- list: List products (GET /admin/products)
- create: Create product (POST /admin/products)
- get_by_id: Get product (GET /admin/products/{id})
- add_products: Update product (POST /admin/products/{id})
- delete: Delete product (DELETE /admin/products/{id})
- list_orders: List orders (GET /admin/orders)
- list_customers: List customers (GET /admin/customers)
- list_regions: List regions (GET /admin/regions)

## Fields

- `title`: string [REQUIRED for create]
- `is_giftcard`: boolean [OPTIONAL]
- `status`: string [OPTIONAL]

## Example Request Bodies

**Create Product:**
```json
{"title": "Premium T-Shirt", "is_giftcard": false, "status": "published"}
```

**Update Product:**
```json
{"title": "Premium T-Shirt v2", "status": "draft"}
```
