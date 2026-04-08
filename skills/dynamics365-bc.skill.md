---
name: dynamics365-bc
description: Manage customers, items, and invoices via Dynamics 365 Business Central.
  Use when the user mentions dynamics 365 business central, business central, erp,
  invoice, item, customer.
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
compatibility: Requires DYNAMICS365_BC_BASE_URL and DYNAMICS365_BC_ACCESS_TOKEN environment
  variables.
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
- list_itemcards: List items (GET /v2.0/companies/{companyId}/itemCards)
- create_itemcards: Create an item (POST /v2.0/companies/{companyId}/itemCards)
- get_by_id_itemcards: Get item by ID (GET /v2.0/companies/{companyId}/itemCards/{id})
- delete_itemcards: Delete an item (DELETE /v2.0/companies/{companyId}/itemCards/{id})
- update_itemcards: Update an item (PATCH /v2.0/companies/{companyId}/itemCards/{id})
- list_salesinvoices: List sales invoices (GET /v2.0/companies/{companyId}/salesInvoices)
- create_salesinvoices: Create a sales invoice (POST /v2.0/companies/{companyId}/salesInvoices)
- list_companies: List companies (GET /v2.0/companies)
- list_vendors: List vendors (GET /v2.0/companies/{companyId}/vendors)
- list_companies_2: Returns a list of companies (GET /companies)

## Fields

- `displayName`: string [REQUIRED for create customer/item]
- `number`: string [OPTIONAL] (customer or item number)
- `email`: string [OPTIONAL] (customer email address)
- `phoneNumber`: string [OPTIONAL] (customer phone number)
- `companyId`: string [REQUIRED] (company GUID for all operations)
- `unitPrice`: number [REQUIRED for create item] (item unit price)
- `type`: string [OPTIONAL for create item] ("Inventory", "Service", "Non-Inventory")
- `customerId`: string [REQUIRED for create invoice] (customer ID for sales invoice)
- `invoiceDate`: string [OPTIONAL] (invoice date in ISO format)
- `currencyCode`: string [OPTIONAL] (e.g., "USD", "EUR")

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
