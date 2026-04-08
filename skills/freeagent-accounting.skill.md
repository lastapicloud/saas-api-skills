---
name: freeagent-accounting
description: Manage invoices, contacts, and expenses via FreeAgent. Use when the user
  mentions freeagent, accounting, invoice, expense, contact, bank.
version: 1.0.0
skill_type: external
base_url_env: FREEAGENT_BASE_URL
auth_env_var: FREEAGENT_ACCESS_TOKEN
auth_type: bearer
triggers:
  - freeagent
  - accounting
  - invoice
  - expense
  - contact
  - bank
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires FREEAGENT_BASE_URL and FREEAGENT_ACCESS_TOKEN environment
  variables.
---

# Freeagent-Accounting

Manage invoices, contacts, and expenses via FreeAgent. Use when the user mentions freeagent, accounting, invoice, expense, contact, bank.

## API Endpoints

- **GET** `/v2/invoices` - List invoices
- **POST** `/v2/invoices` - Create invoice
- **GET** `/v2/invoices/{id}` - Get invoice
- **PUT** `/v2/invoices/{id}` - Update invoice
- **GET** `/v2/contacts` - List contacts
- **POST** `/v2/contacts` - Create contact
- **GET** `/v2/expenses` - List expenses
- **POST** `/v2/expenses` - Create expense

## Actions

- list: List invoices (GET /v2/invoices)
- create: Create invoice (POST /v2/invoices)
- get_by_id: Get invoice (GET /v2/invoices/{id})
- update: Update invoice (PUT /v2/invoices/{id})
- list_contacts: List contacts (GET /v2/contacts)
- create_contacts: Create contact (POST /v2/contacts)
- list_expenses: List expenses (GET /v2/expenses)
- create_expenses: Create expense (POST /v2/expenses)

## Fields

- `contact`: string [REQUIRED for create]
- `dated_on`: string [REQUIRED for create]
- `payment_terms_in_days`: integer [OPTIONAL]

## Example Request Bodies

**Create Invoice:**
```json
{"contact": "https://api.freeagent.com/v2/contacts/123", "dated_on": "2025-06-15", "payment_terms_in_days": 30}
```

**Create Expense:**
```json
{"contact": "https://api.freeagent.com/v2/contacts/123", "dated_on": "2025-06-10", "gross_value": "150.00"}
