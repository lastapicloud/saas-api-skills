---
name: hibob-hr
description: Manage employees and time off via HiBob. Use when the user mentions hibob,
  bob, hr, employee, time off, attendance.
version: 1.0.0
skill_type: external
base_url_env: HIBOB_BASE_URL
auth_env_var: HIBOB_API_TOKEN
auth_type: bearer
triggers:
  - hibob
  - bob
  - hr
  - employee
  - time off
  - attendance
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires HIBOB_BASE_URL and HIBOB_API_TOKEN environment variables.
---

# Hibob-Hr

Manage employees and time off via HiBob. Use when the user mentions hibob, bob, hr, employee, time off, attendance.

## API Endpoints

- **GET** `/v1/people` - List employees
- **POST** `/v1/people` - Create employee
- **GET** `/v1/people/{identifier}` - Get employee
- **PUT** `/v1/people/{identifier}` - Update employee
- **GET** `/v1/timeoff/requests` - List time off requests
- **POST** `/v1/timeoff/requests` - Create time off request
- **GET** `/v1/company/people/fields` - List people fields
- **GET** `/v1/metadata/objects/position` - List positions

## Actions

- list: List employees (GET /v1/people)
- create: Create employee (POST /v1/people)
- get_by_id: Get employee (GET /v1/people/{identifier})
- update: Update employee (PUT /v1/people/{identifier})
- list_requests: List time off requests (GET /v1/timeoff/requests)
- create_requests: Create time off request (POST /v1/timeoff/requests)
- list_fields: List people fields (GET /v1/company/people/fields)
- list_position: List positions (GET /v1/metadata/objects/position)

## Fields

- `firstName`: string [REQUIRED for create]
- `surname`: string [REQUIRED for create]
- `email`: string [REQUIRED for create]

## Example Request Bodies

**Create Employee:**
```json
{"firstName": "Alex", "surname": "Johnson", "email": "alex.johnson@company.com"}
```

**Update Employee:**
```json
{"firstName": "Alex", "surname": "Johnson-Lee", "email": "alex.lee@company.com"}
```
