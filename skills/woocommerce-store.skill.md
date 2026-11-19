---
name: woocommerce-store
description: 'Manage WooCommerce products, orders, and customers. Use when the user
  mentions woocommerce, product, order, customer, e-commerce, wordpress.

  '
version: 1.0.0
skill_type: external
base_url_env: WOOCOMMERCE_BASE_URL
auth_env_var: WOOCOMMERCE_SECRET
auth_user_env: WOOCOMMERCE_KEY
auth_type: basic
triggers:
  - woocommerce
  - product
  - order
  - customer
  - e-commerce
  - wordpress
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires WOOCOMMERCE_BASE_URL and WOOCOMMERCE_SECRET environment variables.
annotations:
  readOnlyHint: false
  destructiveHint: true
  idempotentHint: false
---

# Woocommerce-Store

Manage WooCommerce products, orders, and customers. Use when the user mentions woocommerce, product, order, customer, e-commerce, wordpress.


## API Endpoints

- **GET** `/wp-json/wc/v3/products` - List products
- **GET** `/wp-json/wc/v3/products/{productId}` - Get a product
- **POST** `/wp-json/wc/v3/products` - Create a product
- **PUT** `/wp-json/wc/v3/products/{productId}` - Update a product
- **DELETE** `/wp-json/wc/v3/products/{productId}` - Delete a product
- **GET** `/wp-json/wc/v3/orders` - List orders
- **POST** `/wp-json/wc/v3/orders` - Create an order
- **GET** `/wp-json/wc/v3/customers` - List customers
- **POST** `/wp-json/wc/v3/customers` - Create a customer
- **GET** `/wp-json/wc/v3/reports` - List reports

## Actions

- list: List products (GET /wp-json/wc/v3/products)
- get_by_id: Get a product (GET /wp-json/wc/v3/products/{productId})
- create: Create a product (POST /wp-json/wc/v3/products)
- update: Update a product (PUT /wp-json/wc/v3/products/{productId})
- delete: Delete a product (DELETE /wp-json/wc/v3/products/{productId})
- list_orders: List orders (GET /wp-json/wc/v3/orders)
- create_order: Create an order (POST /wp-json/wc/v3/orders)
- list_customers: List customers (GET /wp-json/wc/v3/customers)
- create_customer: Create a customer (POST /wp-json/wc/v3/customers)
- list_reports: List reports (GET /wp-json/wc/v3/reports)

## Fields

- `name`: string [REQUIRED for create product] — Display name
- `type`: string [OPTIONAL] ("simple", "grouped", "external", "variable") — Resource type
- `regular_price`: string [REQUIRED] — Regular price amount
- `description`: string [OPTIONAL] — Human-readable description
- `sku`: string [OPTIONAL] — Sku

## Example Request Bodies

**Create Product:**
```json
{"name": "Organic Cotton T-Shirt", "type": "simple", "regular_price": "29.99", "description": "100% organic cotton", "sku": "OCT-001"}
```

**Create Customer:**
```json
{"email": "jane@example.com", "first_name": "Jane", "last_name": "Doe"}
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
