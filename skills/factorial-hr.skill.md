---
name: factorial-hr
description: 'Manage employees and time off via Factorial HR. Use when the user mentions
  factorial, hr, employee, time off, leave, attendance.

  '
version: 1.0.0
skill_type: external
base_url_env: FACTORIAL_BASE_URL
auth_env_var: FACTORIAL_API_TOKEN
auth_type: bearer
triggers:
  - factorial
  - hr
  - employee
  - time off
  - leave
  - attendance
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires FACTORIAL_BASE_URL and FACTORIAL_API_TOKEN environment variables.
annotations:
  readOnlyHint: false
  destructiveHint: false
  idempotentHint: false
---

# Factorial-Hr

Manage employees and time off via Factorial HR. Use when the user mentions factorial, hr, employee, time off, leave, attendance.


## API Endpoints

- **GET** `/v1/time/shifts` - Get shifts from a company
- **POST** `/v1/time/leaves` - Create leave
- **PUT** `/v1/time/shifts/{id}` - Update shift
- **DELETE** `/v1/time/shifts/{id}` - Delete shift
- **GET** `/v1/ats/job_postings` - This endpoint allows fetching all available Ats Job Postings, scoped to the user credentials and company of that user
- **POST** `/v1/ats/job_postings` - This endpoint allows you create and store Ats Job Postings in Factorial, while using your own user interface to display
- **PUT** `/v1/ats/job_postings/{id}` - This endpoint allows you to update an existing job posting with new information
- **DELETE** `/v1/ats/job_postings/{id}` - Delete an existing job posting
- **GET** `/v1/payroll/family_situation` - Get all family situations - only FR employees
- **POST** `/v1/payroll/contract_versions` - Create a contract version
- **PATCH** `/v1/payroll/contract_versions/{id}` - Update a contract version
- **DELETE** `/v1/payroll/contract_versions/{id}` - Delete contract versions
- **GET** `/v2/core/employees` - Only can see all the employees' information, will get a restricted version of the payload as a response based on the
- **POST** `/v2/core/employees` - Create employee
- **DELETE** `/v1/core/webhooks` - Deletes a subscription to a webhook

## Actions

- list: Get shifts from a company (GET /v1/time/shifts)
- create: Create leave (POST /v1/time/leaves)
- update: Update shift (PUT /v1/time/shifts/{id})
- delete: Delete shift (DELETE /v1/time/shifts/{id})
- get_this_endpoint_allows_fetching: This endpoint allows fetching all available Ats Job Postings, scoped to the user (GET /v1/ats/job_postings)
- create_this_endpoint_allows_you: This endpoint allows you create and store Ats Job Postings in Factorial, while u (POST /v1/ats/job_postings)
- update_this_endpoint_allows_you: This endpoint allows you to update an existing job posting with new information (PUT /v1/ats/job_postings/{id})
- delete_existing_job_posting: Delete an existing job posting (DELETE /v1/ats/job_postings/{id})
- get_family_situations_only: Get all family situations - only FR employees (GET /v1/payroll/family_situation)
- create_contract_version: Create a contract version (POST /v1/payroll/contract_versions)
- update_contract_version: Update a contract version (PATCH /v1/payroll/contract_versions/{id})
- delete_contract_versions: Delete contract versions (DELETE /v1/payroll/contract_versions/{id})
- get_only_can_see_employees: Only can see all the employees' information, will get a restricted version of th (GET /v2/core/employees)
- create_employee: Create employee (POST /v2/core/employees)
- delete_webhooks: Deletes a subscription to a webhook (DELETE /v1/core/webhooks)

## Fields

- `first_name`: string [REQUIRED for create] — First display name
- `last_name`: string [REQUIRED for create] — Last display name
- `email`: string [REQUIRED for create] — Email address

## Example Request Bodies

**Create Employee:**
```json
{"first_name": "Maria", "last_name": "Garcia", "email": "maria.garcia@company.com"}
```

**Create Leave:**
```json
{"employee_id": 123, "leave_type_id": 1, "start_on": "2025-07-01", "finish_on": "2025-07-05"}

## Response

**Job Posting object:**
- `id`: string — Unique job posting identifier
- `name`: string — Job Posting name or title
- `status`: string — Current status
- `created_at`: string — Creation timestamp (ISO 8601)
- `updated_at`: string — Last update timestamp (ISO 8601)

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
