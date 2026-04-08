---
name: gusto-hr
description: Manage employees, payroll, and benefits via Gusto. Use when the user
  mentions gusto, payroll, employee, hr, benefits, compensation.
version: 1.0.0
skill_type: external
base_url_env: GUSTO_BASE_URL
auth_env_var: GUSTO_ACCESS_TOKEN
auth_type: bearer
triggers:
  - gusto
  - payroll
  - employee
  - hr
  - benefits
  - compensation
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires GUSTO_BASE_URL and GUSTO_ACCESS_TOKEN environment variables.
---

# Gusto-Hr

Manage employees, payroll, and benefits via Gusto. Use when the user mentions gusto, payroll, employee, hr, benefits, compensation.

## API Endpoints

- **GET** `/v1/companies/{company_id}/employees` - List employees
- **POST** `/v1/companies/{company_id}/employees` - Create employee
- **GET** `/v1/employees/{employee_id}` - Get employee
- **PUT** `/v1/employees/{employee_id}` - Update employee
- **GET** `/v1/companies/{company_id}/payrolls` - List payrolls
- **GET** `/v1/companies/{company_id}` - Get company
- **GET** `/v1/companies/{company_id}/locations` - List locations
- **GET** `/v1/employees/{employee_id}/compensations` - List compensations

## Actions

- list: List employees (GET /v1/companies/{company_id}/employees)
- create: Create employee (POST /v1/companies/{company_id}/employees)
- get_by_id: Get employee (GET /v1/employees/{employee_id})
- update: Update employee (PUT /v1/employees/{employee_id})
- list_payrolls: List payrolls (GET /v1/companies/{company_id}/payrolls)
- get_by_id_companies: Get company (GET /v1/companies/{company_id})
- list_locations: List locations (GET /v1/companies/{company_id}/locations)
- list_compensations: List compensations (GET /v1/employees/{employee_id}/compensations)

## Fields

- `first_name`: string [REQUIRED for create]
- `last_name`: string [REQUIRED for create]
- `email`: string [OPTIONAL]

## Example Request Bodies

**Create Employee:**
```json
{"first_name": "Jane", "last_name": "Smith", "email": "jane.smith@company.com"}
```

**Update Employee:**
```json
{"first_name": "Jane", "last_name": "Smith-Johnson", "email": "jane.johnson@company.com"}
```
