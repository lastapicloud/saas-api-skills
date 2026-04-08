---
name: personio-hr-payroll
description: Manage payroll via Personio HR. Use when the user mentions personio hr,
  personio payroll, payroll, salary, compensation.
version: 1.0.0
skill_type: external
base_url_env: PERSONIO_HR_BASE_URL
auth_env_var: PERSONIO_HR_API_TOKEN
auth_type: bearer
triggers:
  - personio hr
  - personio payroll
  - payroll
  - salary
  - compensation
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires PERSONIO_HR_BASE_URL and PERSONIO_HR_API_TOKEN environment
  variables.
---

# Personio-Hr-Payroll

Manage payroll via Personio HR. Use when the user mentions personio hr, personio payroll, payroll, salary, compensation.

## API Endpoints

- **GET** `/v1/company/employees` - List employees
- **GET** `/v1/company/employees/{id}` - Get employee
- **GET** `/v1/company/employees/{id}/absences/balance` - Get absence balance
- **POST** `/v1/company/attendances` - Create attendance
- **PATCH** `/v1/company/attendances/{id}` - Update attendance
- **DELETE** `/v1/company/attendances/{id}` - Delete attendance

## Actions

- list: List employees (GET /v1/company/employees)
- get_by_id: Get employee (GET /v1/company/employees/{id})
- list_balance: Get absence balance (GET /v1/company/employees/{id}/absences/balance)
- create: Create attendance (POST /v1/company/attendances)
- update: Update attendance (PATCH /v1/company/attendances/{id})
- delete: Delete attendance (DELETE /v1/company/attendances/{id})

## Fields

- `employee_id`: integer [REQUIRED]
- `date`: string [REQUIRED for attendance]
- `start_time`: string [OPTIONAL]
- `end_time`: string [OPTIONAL]

## Example Request Bodies

**Create Attendance:**
```json
{"employee_id": 12345, "date": "2024-03-15", "start_time": "09:00", "end_time": "17:30"}
```

**Update Attendance:**
```json
{"employee_id": 12345, "date": "2024-03-15", "start_time": "08:30", "end_time": "17:00"}
```
