---
name: magento-store
description: Manage products, orders, and customers via Magento. Use when the user
  mentions magento, product, order, customer, catalog, ecommerce, e-commerce.
version: 1.0.0
skill_type: external
base_url_env: MAGENTO_BASE_URL
auth_env_var: MAGENTO_ACCESS_TOKEN
auth_type: bearer
triggers:
  - magento
  - product
  - order
  - customer
  - catalog
  - ecommerce
  - e-commerce
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires MAGENTO_BASE_URL and MAGENTO_ACCESS_TOKEN environment variables.
---

# Magento-Store

Manage products, orders, and customers via Magento. Use when the user mentions magento, product, order, customer, catalog, ecommerce, e-commerce.

## API Endpoints

- **GET** `/rest/V1/products` - List products
- **POST** `/rest/V1/products` - Create product
- **GET** `/rest/V1/products/{sku}` - Get product by SKU
- **PUT** `/rest/V1/products/{sku}` - Update product
- **DELETE** `/rest/V1/products/{sku}` - Delete product
- **GET** `/rest/V1/orders` - List orders
- **GET** `/rest/V1/customers/search` - Search customers
- **POST** `/rest/V1/customers` - Create customer
- **GET** `/V1/carts/search` - carts/search
- **POST** `/V1/carts/` - carts/
- **PUT** `/V1/amazon-shipping-address/{amazonOrderReferenceId}` - amazon-shipping-address/{amazonOrderReferenceId}
- **DELETE** `/V1/addresses/{addressId}` - addresses/{addressId}
- **GET** `/V1/cmsBlock/search` - cmsBlock/search
- **GET** `/V1/cmsPage/search` - cmsPage/search

## Actions

- list: List products (GET /rest/V1/products)
- create: Create product (POST /rest/V1/products)
- get_by_id: Get product by SKU (GET /rest/V1/products/{sku})
- update: Update product (PUT /rest/V1/products/{sku})
- delete: Delete product (DELETE /rest/V1/products/{sku})
- list_orders: List orders (GET /rest/V1/orders)
- search: Search customers (GET /rest/V1/customers/search)
- create_customers: Create customer (POST /rest/V1/customers)
- search_carts: carts/search (GET /V1/carts/search)
- create_carts: carts/ (POST /V1/carts/)
- update_amazon_shipping_address: amazon-shipping-address/{amazonOrderReferenceId} (PUT /V1/amazon-shipping-address/{amazonOrderReferenceId})
- delete_addresses: addresses/{addressId} (DELETE /V1/addresses/{addressId})
- search_cmsblock: cmsBlock/search (GET /V1/cmsBlock/search)
- search_cmspage: cmsPage/search (GET /V1/cmsPage/search)

## Fields

- `sku`: string [REQUIRED for create]
- `name`: string [REQUIRED for create]
- `price`: number [REQUIRED for create]
- `attribute_set_id`: integer [REQUIRED for create]

## Example Request Bodies

**Create Product:**
```json
{"product": {"sku": "SHOE-RED-42", "name": "Red Running Shoes Size 42", "price": 89.99, "attribute_set_id": 4, "type_id": "simple"}}
```

**Create Customer:**
```json
{"customer": {"email": "shopper@example.com", "firstname": "Maria", "lastname": "Garcia", "store_id": 1, "group_id": 1}}
```
