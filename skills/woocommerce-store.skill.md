---
name: woocommerce-store
description: Manage WooCommerce products, orders, and customers. Use when the user
  mentions woocommerce, product, order, customer, e-commerce, wordpress.
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
- create_orders: Create an order (POST /wp-json/wc/v3/orders)
- list_customers: List customers (GET /wp-json/wc/v3/customers)
- create_customers: Create a customer (POST /wp-json/wc/v3/customers)
- list_reports: List reports (GET /wp-json/wc/v3/reports)

## Fields

- `name`: string [REQUIRED for create product]
- `type`: string [OPTIONAL] ("simple", "grouped", "external", "variable")
- `regular_price`: string [REQUIRED]
- `description`: string [OPTIONAL]
- `sku`: string [OPTIONAL]

## Example Request Bodies

**Create Product:**
```json
{"name": "Organic Cotton T-Shirt", "type": "simple", "regular_price": "29.99", "description": "100% organic cotton", "sku": "OCT-001"}
```

**Create Customer:**
```json
{"email": "jane@example.com", "first_name": "Jane", "last_name": "Doe"}
```
