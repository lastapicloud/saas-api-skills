---
name: dynamics365-bc
description: 'Manage customers, items, and invoices via Dynamics 365 Business Central.
  Use when the user mentions dynamics 365 business central, business central, erp,
  invoice, item, customer.

  '
version: 1.0.0
skill_type: external
base_url_env: DYNAMICS365_BC_BASE_URL
auth_env_var: DYNAMICS365_BC_ACCESS_TOKEN
auth_type: bearer
triggers:
  - dynamics 365 business central
  - business central
  - erp
  - invoice
  - item
  - customer
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: 'Requires DYNAMICS365_BC_BASE_URL and DYNAMICS365_BC_ACCESS_TOKEN environment
  variables.

  '
annotations:
  readOnlyHint: false
  destructiveHint: true
  idempotentHint: false
---

# Dynamics365-Bc

Manage customers, items, and invoices via Dynamics 365 Business Central. Use when the user mentions dynamics 365 business central, business central, erp, invoice, item, customer.


## API Endpoints

- **GET** `/v2.0/companies/{companyId}/customers` - List customers
- **POST** `/v2.0/companies/{companyId}/customers` - Create a customer
- **GET** `/v2.0/companies/{companyId}/customers/{id}` - Get customer by ID
- **DELETE** `/v2.0/companies/{companyId}/customers/{id}` - Delete a customer
- **PATCH** `/v2.0/companies/{companyId}/customers/{id}` - Update a customer
- **GET** `/v2.0/companies/{companyId}/itemCards` - List items
- **POST** `/v2.0/companies/{companyId}/itemCards` - Create an item
- **GET** `/v2.0/companies/{companyId}/itemCards/{id}` - Get item by ID
- **DELETE** `/v2.0/companies/{companyId}/itemCards/{id}` - Delete an item
- **PATCH** `/v2.0/companies/{companyId}/itemCards/{id}` - Update an item
- **GET** `/v2.0/companies/{companyId}/salesInvoices` - List sales invoices
- **POST** `/v2.0/companies/{companyId}/salesInvoices` - Create a sales invoice
- **GET** `/v2.0/companies` - List companies
- **GET** `/v2.0/companies/{companyId}/vendors` - List vendors
- **GET** `/companies` - Returns a list of companies

## Actions

- list: List customers (GET /v2.0/companies/{companyId}/customers)
- create: Create a customer (POST /v2.0/companies/{companyId}/customers)
- get_by_id: Get customer by ID (GET /v2.0/companies/{companyId}/customers/{id})
- delete: Delete a customer (DELETE /v2.0/companies/{companyId}/customers/{id})
- update: Update a customer (PATCH /v2.0/companies/{companyId}/customers/{id})
- list_items: List items (GET /v2.0/companies/{companyId}/itemCards)
- create_item: Create an item (POST /v2.0/companies/{companyId}/itemCards)
- get_item_id: Get item by ID (GET /v2.0/companies/{companyId}/itemCards/{id})
- delete_item: Delete an item (DELETE /v2.0/companies/{companyId}/itemCards/{id})
- update_item: Update an item (PATCH /v2.0/companies/{companyId}/itemCards/{id})
- list_sales_invoices: List sales invoices (GET /v2.0/companies/{companyId}/salesInvoices)
- create_sales_invoice: Create a sales invoice (POST /v2.0/companies/{companyId}/salesInvoices)
- list_companies: List companies (GET /v2.0/companies)
- list_vendors: List vendors (GET /v2.0/companies/{companyId}/vendors)
- get_list_companies: Returns a list of companies (GET /companies)

## Fields

- `displayName`: string [REQUIRED for create customer/item] — Display display name
- `number`: string [OPTIONAL] (customer or item number) — Number
- `email`: string [OPTIONAL] (customer email address) — Email address
- `phoneNumber`: string [OPTIONAL] (customer phone number) — Phonenumber
- `companyId`: string [REQUIRED] (company GUID for all operations) — Company unique identifier
- `unitPrice`: number [REQUIRED for create item] (item unit price) — Unit price amount
- `type`: string [OPTIONAL for create item] ("Inventory", "Service", "Non-Inventory") — Resource type
- `customerId`: string [REQUIRED for create invoice] (customer ID for sales invoice) — Customer unique identifier
- `invoiceDate`: string [OPTIONAL] (invoice date in ISO format) — Invoicedate
- `currencyCode`: string [OPTIONAL] (e.g., "USD", "EUR") — Currencycode

## Example Request Bodies

**Create a Customer:**
```json
{
  "displayName": "Contoso Ltd",
  "email": "info@contoso.com",
  "phoneNumber": "+1-555-0100",
  "currencyCode": "USD"
}
```

**Create an Item:**
```json
{
  "displayName": "Standard Widget",
  "number": "ITEM-001",
  "unitPrice": 29.99,
  "type": "Inventory"
}
```

## Response

**Customer object:**
- `id`: string — Unique customer identifier
- `name`: string — Customer name or title
- `status`: string — Current status
- `created_at`: string — Creation timestamp (ISO 8601)
- `updated_at`: string — Last update timestamp (ISO 8601)


**Required fields reference:**
```json
{
  "companyId": "example_companyId",
  "customerId": "example_customerId"
}
```


**Required fields reference:**
```json
{
  "companyId": "example_companyId",
  "customerId": "example_customerId"
}
```

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
