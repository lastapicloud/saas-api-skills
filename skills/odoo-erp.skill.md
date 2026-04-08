---
name: odoo-erp
description: Manage records via Odoo ERP. Use when the user mentions odoo, erp, crm,
  invoice, product, sale order, purchase.
version: 1.0.0
skill_type: external
base_url_env: ODOO_BASE_URL
auth_env_var: ODOO_API_KEY
auth_type: bearer
triggers:
  - odoo
  - erp
  - crm
  - invoice
  - product
  - sale order
  - purchase
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires ODOO_BASE_URL and ODOO_API_KEY environment variables.
---

# Odoo-Erp

Manage records via Odoo ERP. Use when the user mentions odoo, erp, crm, invoice, product, sale order, purchase.

## API Endpoints

- **POST** `/web/dataset/call_kw` - Call model method
- **POST** `/web/dataset/search_read` - Search and read records
- **POST** `/jsonrpc` - JSON-RPC call
- **GET** `/api/v1/{model}` - List records
- **POST** `/api/v1/{model}` - Create record
- **GET** `/api/v1/{model}/{id}` - Get record
- **PUT** `/api/v1/{model}/{id}` - Update record
- **DELETE** `/api/v1/{model}/{id}` - Delete record
- **GET** `/api/2/materials` - Voodoo Manufacturing offers printing in a number of different materials, with different color options for each. Your
- **GET** `/api/2/model` - Retrieve the models you've created.
- **GET** `/api/2/order` - Lists all orders.
- **POST** `/api/2/model` - Models represent 3D design files that you'd like to produce. Creating models is generally the first step in creating an
- **GET** `/api/2/model/quote` - Get a quote a given model id.
- **GET** `/api/2/model/quote_attrs` - Get a quote for a model with the given attributes.
- **POST** `/api/2/order/confirm` - Confirms an order from a quote_id and submits it to the Voodoo factory.

## Actions

- create: Call model method (POST /web/dataset/call_kw)
- search: Search and read records (POST /web/dataset/search_read)
- create_jsonrpc: JSON-RPC call (POST /jsonrpc)
- get_by_id: List records (GET /api/v1/{model})
- add_v1: Create record (POST /api/v1/{model})
- get_by_id_v1: Get record (GET /api/v1/{model}/{id})
- update: Update record (PUT /api/v1/{model}/{id})
- delete: Delete record (DELETE /api/v1/{model}/{id})
- list: Voodoo Manufacturing offers printing in a number of different materials, with di (GET /api/2/materials)
- list_model: Retrieve the models you've created. (GET /api/2/model)
- list_order: Lists all orders. (GET /api/2/order)
- create_model: Models represent 3D design files that you'd like to produce. Creating models is (POST /api/2/model)
- list_quote: Get a quote a given model id. (GET /api/2/model/quote)
- list_quote_attrs: Get a quote for a model with the given attributes. (GET /api/2/model/quote_attrs)
- create_confirm: Confirms an order from a quote_id and submits it to the Voodoo factory. (POST /api/2/order/confirm)

## Fields

- `model`: string [REQUIRED]
- `domain`: array [OPTIONAL for search]
- `fields`: array [OPTIONAL]
- `values`: object [REQUIRED for create]

## Example Request Bodies

**Search and Read Records:**
```json
{"model": "res.partner", "domain": [["is_company", "=", true]], "fields": ["name", "email", "phone"]}
```

**Call Model Method (Create):**
```json
{"model": "res.partner", "method": "create", "args": [{"name": "Acme Corp", "email": "info@acme.com"}], "kwargs": {}}
```
