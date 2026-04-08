---
name: factorial-hr
description: Manage employees and time off via Factorial HR. Use when the user mentions
  factorial, hr, employee, time off, leave, attendance.
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
---

# Factorial-Hr

Manage employees and time off via Factorial HR. Use when the user mentions factorial, hr, employee, time off, leave, attendance.

## API Endpoints

- **GET** `/api/2.0/core/employees` - List employees
- **POST** `/api/2.0/core/employees` - Create employee
- **GET** `/api/2.0/core/employees/{id}` - Get employee
- **PUT** `/api/2.0/core/employees/{id}` - Update employee
- **GET** `/api/2.0/time/leaves` - List leaves
- **POST** `/api/2.0/time/leaves` - Create leave
- **GET** `/api/2.0/time/shifts` - List shifts
- **GET** `/api/2.0/core/teams` - List teams

## Actions

- list: List employees (GET /api/2.0/core/employees)
- create: Create employee (POST /api/2.0/core/employees)
- get_by_id: Get employee (GET /api/2.0/core/employees/{id})
- update: Update employee (PUT /api/2.0/core/employees/{id})
- list_leaves: List leaves (GET /api/2.0/time/leaves)
- create_leaves: Create leave (POST /api/2.0/time/leaves)
- list_shifts: List shifts (GET /api/2.0/time/shifts)
- list_teams: List teams (GET /api/2.0/core/teams)

## Fields

- `first_name`: string [REQUIRED for create]
- `last_name`: string [REQUIRED for create]
- `email`: string [REQUIRED for create]

## Example Request Bodies

**Create Employee:**
```json
{"first_name": "Maria", "last_name": "Garcia", "email": "maria.garcia@company.com"}
```

**Create Leave:**
```json
{"employee_id": 123, "leave_type_id": 1, "start_on": "2025-07-01", "finish_on": "2025-07-05"}
