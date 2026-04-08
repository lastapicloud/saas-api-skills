---
name: xero-accounting
description: Manage Xero invoices, contacts, and accounts. Use when the user mentions
  xero, invoice, contact, accounting, payment, bank.
version: 1.0.0
skill_type: external
base_url_env: XERO_BASE_URL
auth_env_var: XERO_ACCESS_TOKEN
auth_type: bearer
triggers:
  - xero
  - invoice
  - contact
  - accounting
  - payment
  - bank
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires XERO_BASE_URL and XERO_ACCESS_TOKEN environment variables.
---

# Xero-Accounting

Manage Xero invoices, contacts, and accounts. Use when the user mentions xero, invoice, contact, accounting, payment, bank.

## API Endpoints

- **GET** `/api.xro/2.0/Invoices` - List invoices
- **GET** `/api.xro/2.0/Invoices/{InvoiceID}` - Get an invoice
- **POST** `/api.xro/2.0/Invoices` - Create an invoice
- **PUT** `/api.xro/2.0/Invoices/{InvoiceID}` - Update an invoice
- **GET** `/api.xro/2.0/Contacts` - List contacts
- **POST** `/api.xro/2.0/Contacts` - Create a contact
- **GET** `/api.xro/2.0/Accounts` - List accounts
- **GET** `/api.xro/2.0/Payments` - List payments
- **POST** `/api.xro/2.0/Payments` - Create a payment
- **GET** `/api.xro/2.0/Organisation` - Get organisation info
- **GET** `/FeedConnections` - Searches for feed connections
- **GET** `/Statements` - Retrieve all statements
- **POST** `/FeedConnections` - Create one or more new feed connection
- **POST** `/FeedConnections/DeleteRequests` - Delete an existing feed connection
- **POST** `/Statements` - Creates one or more new statements

## Actions

- list: List invoices (GET /api.xro/2.0/Invoices)
- get_by_id: Get an invoice (GET /api.xro/2.0/Invoices/{InvoiceID})
- create: Create an invoice (POST /api.xro/2.0/Invoices)
- update: Update an invoice (PUT /api.xro/2.0/Invoices/{InvoiceID})
- list_contacts: List contacts (GET /api.xro/2.0/Contacts)
- create_contacts: Create a contact (POST /api.xro/2.0/Contacts)
- list_accounts: List accounts (GET /api.xro/2.0/Accounts)
- list_payments: List payments (GET /api.xro/2.0/Payments)
- create_payments: Create a payment (POST /api.xro/2.0/Payments)
- list_organisation: Get organisation info (GET /api.xro/2.0/Organisation)
- list_feedconnections: Searches for feed connections (GET /FeedConnections)
- list_statements: Retrieve all statements (GET /Statements)
- create_feedconnections: Create one or more new feed connection (POST /FeedConnections)
- create_deleterequests: Delete an existing feed connection (POST /FeedConnections/DeleteRequests)
- create_statements: Creates one or more new statements (POST /Statements)

## Fields

- `Type`: string [REQUIRED for create invoice] ("ACCREC" or "ACCPAY")
- `Contact`: object [REQUIRED] with `Name`
- `LineItems`: array [REQUIRED] with `Description`, `Quantity`, `UnitAmount`
- `Date`: string [OPTIONAL]
- `DueDate`: string [OPTIONAL]

## Example Request Bodies

**Create Invoice:**
```json
{"Type": "ACCREC", "Contact": {"Name": "Acme Corp"}, "LineItems": [{"Description": "Consulting Services", "Quantity": 10, "UnitAmount": 150.00}], "DueDate": "2026-04-30"}
```

**Create Contact:**
```json
{"Name": "New Client LLC", "EmailAddress": "billing@newclient.com"}
