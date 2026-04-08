---
name: freshbooks-accounting
description: Manage FreshBooks invoices, clients, and expenses. Use when the user
  mentions freshbooks, invoice, client, expense, accounting.
version: 1.0.0
skill_type: external
base_url_env: FRESHBOOKS_BASE_URL
auth_env_var: FRESHBOOKS_ACCESS_TOKEN
auth_type: bearer
triggers:
  - freshbooks
  - invoice
  - client
  - expense
  - accounting
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires FRESHBOOKS_BASE_URL and FRESHBOOKS_ACCESS_TOKEN environment
  variables.
---

# Freshbooks-Accounting

Manage FreshBooks invoices, clients, and expenses. Use when the user mentions freshbooks, invoice, client, expense, accounting.

## API Endpoints

- **GET** `/accounting/account/{accountId}/invoices/invoices` - List invoices
- **GET** `/accounting/account/{accountId}/invoices/invoices/{invoiceId}` - Get an invoice
- **POST** `/accounting/account/{accountId}/invoices/invoices` - Create an invoice
- **PUT** `/accounting/account/{accountId}/invoices/invoices/{invoiceId}` - Update an invoice
- **DELETE** `/accounting/account/{accountId}/invoices/invoices/{invoiceId}` - Delete an invoice
- **GET** `/accounting/account/{accountId}/users/clients` - List clients
- **POST** `/accounting/account/{accountId}/users/clients` - Create a client
- **GET** `/accounting/account/{accountId}/expenses/expenses` - List expenses
- **POST** `/accounting/account/{accountId}/expenses/expenses` - Create an expense
- **GET** `/auth/api/v1/users/me` - Get current user

## Actions

- list: List invoices (GET /accounting/account/{accountId}/invoices/invoices)
- get_by_id: Get an invoice (GET /accounting/account/{accountId}/invoices/invoices/{invoiceId})
- create: Create an invoice (POST /accounting/account/{accountId}/invoices/invoices)
- update: Update an invoice (PUT /accounting/account/{accountId}/invoices/invoices/{invoiceId})
- delete: Delete an invoice (DELETE /accounting/account/{accountId}/invoices/invoices/{invoiceId})
- list_clients: List clients (GET /accounting/account/{accountId}/users/clients)
- create_clients: Create a client (POST /accounting/account/{accountId}/users/clients)
- list_expenses: List expenses (GET /accounting/account/{accountId}/expenses/expenses)
- create_expenses: Create an expense (POST /accounting/account/{accountId}/expenses/expenses)
- list_me: Get current user (GET /auth/api/v1/users/me)

## Fields

- `invoice`: object [REQUIRED for create] with `customerid`, `create_date`
- `lines`: array [REQUIRED for invoice] with `name`, `amount`, `qty`
- `client`: object [REQUIRED for create client] with `fname`, `lname`, `email`
- `expense`: object [REQUIRED for create expense] with `amount`, `categoryid`

## Example Request Bodies

**Create Invoice:**
```json
{"invoice": {"customerid": 123, "create_date": "2025-06-15"}, "lines": [{"name": "Consulting", "amount": {"amount": "500.00"}, "qty": 1}]}
```

**Create Client:**
```json
{"client": {"fname": "John", "lname": "Doe", "email": "john@example.com"}}
