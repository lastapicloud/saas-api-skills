---
name: commercetools-commerce
description: Manage products, orders, and customers via commercetools. Use when the
  user mentions commercetools, product, order, customer, cart, commerce, ecommerce.
version: 1.0.0
skill_type: external
base_url_env: COMMERCETOOLS_BASE_URL
auth_env_var: COMMERCETOOLS_ACCESS_TOKEN
auth_type: bearer
triggers:
  - commercetools
  - product
  - order
  - customer
  - cart
  - commerce
  - ecommerce
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires COMMERCETOOLS_BASE_URL and COMMERCETOOLS_ACCESS_TOKEN environment
  variables.
---

# Commercetools-Commerce

Manage products, orders, and customers via commercetools. Use when the user mentions commercetools, product, order, customer, cart, commerce, ecommerce.

## API Endpoints

- **GET** `/{projectKey}/products` - List products
- **POST** `/{projectKey}/products` - Create a product
- **GET** `/{projectKey}/products/{ID}` - Get product by ID
- **GET** `/{projectKey}/orders` - List orders
- **POST** `/{projectKey}/orders` - Create an order
- **GET** `/{projectKey}/customers` - List customers
- **POST** `/{projectKey}/customers` - Create a customer
- **GET** `/{projectKey}/carts` - List carts

## Actions

- list: List products (GET /{projectKey}/products)
- create: Create a product (POST /{projectKey}/products)
- get_by_id: Get product by ID (GET /{projectKey}/products/{ID})
- list_orders: List orders (GET /{projectKey}/orders)
- create_orders: Create an order (POST /{projectKey}/orders)
- list_customers: List customers (GET /{projectKey}/customers)
- create_customers: Create a customer (POST /{projectKey}/customers)
- list_carts: List carts (GET /{projectKey}/carts)

## Fields

- `name`: object [REQUIRED for create] (localized string)
- `productType`: object [REQUIRED for create]
- `slug`: object [REQUIRED for create]

## Example Request Bodies

**Create Product:**
```json
{"name": {"en": "Wireless Mouse"}, "productType": {"id": "pt-abc123", "typeId": "product-type"}, "slug": {"en": "wireless-mouse"}}
```

**Create Customer:**
```json
{"email": "john.doe@example.com", "firstName": "John", "lastName": "Doe", "password": "securePass123"}
```
