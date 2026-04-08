---
name: ecwid-store
description: Manage products and orders via Ecwid e-commerce. Use when the user mentions
  ecwid, product, order, store, ecommerce.
version: 1.0.0
skill_type: external
base_url_env: ECWID_BASE_URL
auth_env_var: ECWID_API_TOKEN
auth_type: bearer
triggers:
  - ecwid
  - product
  - order
  - store
  - ecommerce
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires ECWID_BASE_URL and ECWID_API_TOKEN environment variables.
---

# Ecwid-Store

Manage products and orders via Ecwid e-commerce. Use when the user mentions ecwid, product, order, store, ecommerce.

## API Endpoints

- **GET** `/api/v3/{storeId}/products` - List products
- **POST** `/api/v3/{storeId}/products` - Create product
- **GET** `/api/v3/{storeId}/products/{productId}` - Get product
- **PUT** `/api/v3/{storeId}/products/{productId}` - Update product
- **DELETE** `/api/v3/{storeId}/products/{productId}` - Delete product
- **GET** `/api/v3/{storeId}/orders` - List orders
- **GET** `/api/v3/{storeId}/customers` - List customers
- **GET** `/elements/api-v2/customers` - Find customers in the eCommerce system, using the provided CEQL search expression. If no search expression is provided,
- **POST** `/elements/api-v2/bulk/query` - Create an asynchronous bulk query job.
- **PUT** `/elements/api-v2/bulk/{id}/cancel` - Cancel an asynchronous bulk query job.
- **PATCH** `/elements/api-v2/customers/{id}` - Update an customer associated with a given ID in the eCommerce system.The update API uses the PATCH HTTP verb, so only
- **DELETE** `/elements/api-v2/customers/{id}` - Delete a customer associated with a given ID from your eCommerce system. Specifying a customer associated with a given
- **GET** `/elements/api-v2/objects` - Get a list of all the available objects.

## Actions

- list: List products (GET /api/v3/{storeId}/products)
- create: Create product (POST /api/v3/{storeId}/products)
- get_by_id: Get product (GET /api/v3/{storeId}/products/{productId})
- update: Update product (PUT /api/v3/{storeId}/products/{productId})
- delete: Delete product (DELETE /api/v3/{storeId}/products/{productId})
- list_orders: List orders (GET /api/v3/{storeId}/orders)
- list_customers: List customers (GET /api/v3/{storeId}/customers)
- list_customers_2: Find customers in the eCommerce system, using the provided CEQL search expressio (GET /elements/api-v2/customers)
- query: Create an asynchronous bulk query job. (POST /elements/api-v2/bulk/query)
- put_cancel: Cancel an asynchronous bulk query job. (PUT /elements/api-v2/bulk/{id}/cancel)
- update_customers: Update an customer associated with a given ID in the eCommerce system.The update (PATCH /elements/api-v2/customers/{id})
- delete_customers: Delete a customer associated with a given ID from your eCommerce system. Specify (DELETE /elements/api-v2/customers/{id})
- list_objects: Get a list of all the available objects. (GET /elements/api-v2/objects)

## Fields

- `name`: string [REQUIRED for create]
- `price`: number [REQUIRED for create]
- `sku`: string [OPTIONAL]

## Example Request Bodies

**Create Product:**
```json
{"name": "Wireless Mouse", "price": 24.99, "sku": "WM-001"}
```

**Update Product:**
```json
{"name": "Wireless Mouse Pro", "price": 34.99}
