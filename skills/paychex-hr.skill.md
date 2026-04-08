---
name: paychex-hr
description: Manage employees and payroll via Paychex. Use when the user mentions
  paychex, payroll, employee, hr, worker, compensation.
version: 1.0.0
skill_type: external
base_url_env: PAYCHEX_BASE_URL
auth_env_var: PAYCHEX_ACCESS_TOKEN
auth_type: bearer
triggers:
  - paychex
  - payroll
  - employee
  - hr
  - worker
  - compensation
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires PAYCHEX_BASE_URL and PAYCHEX_ACCESS_TOKEN environment variables.
---

# Paychex-Hr

Manage employees and payroll via Paychex. Use when the user mentions paychex, payroll, employee, hr, worker, compensation.

## API Endpoints

- **GET** `/companies/{companyId}/workers` - List workers
- **POST** `/companies/{companyId}/workers` - Create worker
- **GET** `/workers/{workerId}` - Get worker
- **PATCH** `/workers/{workerId}` - Update worker
- **GET** `/companies/{companyId}/payperiods` - List pay periods
- **GET** `/companies/{companyId}/checks` - List checks
- **GET** `/companies/{companyId}` - Get company
- **GET** `/workers/{workerId}/compensations` - List compensations

## Actions

- list: List workers (GET /companies/{companyId}/workers)
- create: Create worker (POST /companies/{companyId}/workers)
- get_by_id: Get worker (GET /workers/{workerId})
- update: Update worker (PATCH /workers/{workerId})
- list_payperiods: List pay periods (GET /companies/{companyId}/payperiods)
- list_checks: List checks (GET /companies/{companyId}/checks)
- get_by_id_companies: Get company (GET /companies/{companyId})
- list_compensations: List compensations (GET /workers/{workerId}/compensations)

## Fields

- `givenName`: string [REQUIRED for create]
- `familyName`: string [REQUIRED for create]
- `companyId`: string [REQUIRED]

## Example Request Bodies

**Create Worker:**
```json
{"givenName": "Sarah", "familyName": "Connor", "companyId": "comp-12345"}
```

**Update Worker:**
```json
{"givenName": "Sarah", "familyName": "Connor-Reese"}
```
