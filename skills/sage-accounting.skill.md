---
name: sage-accounting
description: Manage invoices and contacts via Sage. Use when the user mentions sage,
  accounting, invoice, contact, ledger, bank.
version: 1.0.0
skill_type: external
base_url_env: SAGE_BASE_URL
auth_env_var: SAGE_ACCESS_TOKEN
auth_type: bearer
triggers:
  - sage
  - accounting
  - invoice
  - contact
  - ledger
  - bank
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires SAGE_BASE_URL and SAGE_ACCESS_TOKEN environment variables.
---

# Sage-Accounting

Manage invoices and contacts via Sage. Use when the user mentions sage, accounting, invoice, contact, ledger, bank.

## API Endpoints

- **GET** `/contacts` - List contacts
- **POST** `/contacts` - Create contact
- **GET** `/contacts/{key}` - Get contact
- **PUT** `/contacts/{key}` - Update contact
- **DELETE** `/contacts/{key}` - Delete contact
- **GET** `/sales_invoices` - List sales invoices
- **POST** `/sales_invoices` - Create sales invoice
- **GET** `/ledger_accounts` - List ledger accounts
- **GET** `/Subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.RecoveryServices/vaults/{vaultName}/usages` - Fetches the usages of the vault.

## Actions

- list: List contacts (GET /contacts)
- create: Create contact (POST /contacts)
- get_by_id: Get contact (GET /contacts/{key})
- update: Update contact (PUT /contacts/{key})
- delete: Delete contact (DELETE /contacts/{key})
- list_sales_invoices: List sales invoices (GET /sales_invoices)
- create_sales_invoices: Create sales invoice (POST /sales_invoices)
- list_ledger_accounts: List ledger accounts (GET /ledger_accounts)
- list_usages: Fetches the usages of the vault. (GET /Subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.RecoveryServices/vaults/{vaultName}/usages)

## Fields

- `name`: string [REQUIRED for create]
- `contact_type_ids`: array [REQUIRED for create]

## Example Request Bodies

**Create Contact:**
```json
{"name": "Acme Corp", "contact_type_ids": ["CUSTOMER"]}
```

**Create Sales Invoice:**
```json
{"contact_id": "abc123", "date": "2026-03-24", "invoice_lines": [{"description": "Consulting", "quantity": 1, "unit_price": 5000}]}
```
