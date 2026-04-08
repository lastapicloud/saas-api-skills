---
name: deel-hr
description: Manage contracts, workers, and payments via Deel. Use when the user mentions
  deel, contractor, employee, contract, payment, payroll, hr.
version: 1.0.0
skill_type: external
base_url_env: DEEL_BASE_URL
auth_env_var: DEEL_API_TOKEN
auth_type: bearer
triggers:
  - deel
  - contractor
  - employee
  - contract
  - payment
  - payroll
  - hr
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires DEEL_BASE_URL and DEEL_API_TOKEN environment variables.
---

# Deel-Hr

Manage contracts, workers, and payments via Deel. Use when the user mentions deel, contractor, employee, contract, payment, payroll, hr.

## API Endpoints

- **GET** `/rest/v2/contracts` - List contracts
- **POST** `/rest/v2/contracts` - Create a contract
- **GET** `/rest/v2/contracts/{contractId}` - Get contract by ID
- **GET** `/rest/v2/people` - List people
- **GET** `/rest/v2/invoices` - List invoices
- **POST** `/rest/v2/invoices/{invoiceId}/approve` - Approve an invoice
- **GET** `/rest/v2/payments` - List payments
- **GET** `/rest/v2/organizations` - List organizations
- **DELETE** `/rest/v2/contracts/{contractId}` - Terminate a contract

## Actions

- list: List contracts (GET /rest/v2/contracts)
- create: Create a contract (POST /rest/v2/contracts)
- get_by_id: Get contract by ID (GET /rest/v2/contracts/{contractId})
- list_people: List people (GET /rest/v2/people)
- list_invoices: List invoices (GET /rest/v2/invoices)
- create_approve: Approve an invoice (POST /rest/v2/invoices/{invoiceId}/approve)
- list_payments: List payments (GET /rest/v2/payments)
- list_organizations: List organizations (GET /rest/v2/organizations)
- delete: Terminate a contract (DELETE /rest/v2/contracts/{contractId})

## Fields

- `type`: string [REQUIRED for create]
- `title`: string [REQUIRED for create]
- `currency`: string [REQUIRED for create]

## Example Request Bodies

**Create Contract:**
```json
{"type": "contractor", "title": "Senior Frontend Developer", "currency": "USD", "rate": 85.00}
```

**Approve Invoice:**
```json
{"invoiceId": "inv-2026-0412"}
```
