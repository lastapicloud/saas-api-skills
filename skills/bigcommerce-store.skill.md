---
name: bigcommerce-store
description: 'Manage products, orders, and customers via BigCommerce. Use when the
  user mentions bigcommerce, product, order, customer, store, ecommerce, e-commerce.

  '
version: 1.0.0
skill_type: external
base_url_env: BIGCOMMERCE_BASE_URL
auth_env_var: BIGCOMMERCE_ACCESS_TOKEN
auth_type: header
triggers:
  - bigcommerce
  - product
  - order
  - customer
  - store
  - ecommerce
  - e-commerce
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: 'Requires BIGCOMMERCE_BASE_URL and BIGCOMMERCE_ACCESS_TOKEN environment
  variables.

  '
annotations:
  readOnlyHint: false
  destructiveHint: true
  idempotentHint: false
---

# Bigcommerce-Store

Manage products, orders, and customers via BigCommerce. Use when the user mentions bigcommerce, product, order, customer, store, ecommerce, e-commerce.


## API Endpoints

- **GET** `/v3/catalog/products` - List products
- **POST** `/v3/catalog/products` - Create a product
- **GET** `/v3/catalog/products/{product_id}` - Get product by ID
- **PUT** `/v3/catalog/products/{product_id}` - Update a product
- **DELETE** `/v3/catalog/products/{product_id}` - Delete a product
- **GET** `/v2/orders` - List orders
- **GET** `/v3/customers` - List customers
- **POST** `/v3/customers` - Create customers

## Actions

- list: List products (GET /v3/catalog/products)
- create: Create a product (POST /v3/catalog/products)
- get_by_id: Get product by ID (GET /v3/catalog/products/{product_id})
- update: Update a product (PUT /v3/catalog/products/{product_id})
- delete: Delete a product (DELETE /v3/catalog/products/{product_id})
- list_orders: List orders (GET /v2/orders)
- list_customers: List customers (GET /v3/customers)
- create_customers: Create customers (POST /v3/customers)

## Fields

- `name`: string [REQUIRED for create] — Display name
- `type`: string [REQUIRED for create] (physical, digital) — Resource type
- `weight`: number [REQUIRED for create] — Weight
- `price`: number [REQUIRED for create] — Price amount

## Example Request Bodies

**Create Product:**
```json
{"name": "Classic T-Shirt", "type": "physical", "weight": 0.5, "price": 29.99}
```

**Update Product:**
```json
{"name": "Premium T-Shirt", "price": 39.99}

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
