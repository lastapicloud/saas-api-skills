---
name: hibob-hr
description: 'Manage employees and time off via HiBob. Use when the user mentions
  hibob, bob, hr, employee, time off, attendance.

  '
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
annotations:
  readOnlyHint: false
  destructiveHint: false
  idempotentHint: false
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
- list_time_off_requests: List time off requests (GET /v1/timeoff/requests)
- create_time_off_request: Create time off request (POST /v1/timeoff/requests)
- list_people_fields: List people fields (GET /v1/company/people/fields)
- list_positions: List positions (GET /v1/metadata/objects/position)

## Fields

- `firstName`: string [REQUIRED for create] — First display name
- `surname`: string [REQUIRED for create] — Sur display name
- `email`: string [REQUIRED for create] — Email address

## Example Request Bodies

**Create Employee:**
```json
{"firstName": "Alex", "surname": "Johnson", "email": "alex.johnson@company.com"}
```

**Update Employee:**
```json
{"firstName": "Alex", "surname": "Johnson-Lee", "email": "alex.lee@company.com"}
```

## Response

**People object:**
- `id`: string — Unique people identifier
- `name`: string — People name or title
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
