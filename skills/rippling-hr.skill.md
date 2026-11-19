---
name: rippling-hr
description: "Manage Rippling employees, departments, and groups. Use when the user mentions rippling, employee, HR, department, group."
version: 1.0.0
skill_type: external
base_url_env: RIPPLING_BASE_URL
auth_env_var: RIPPLING_API_TOKEN
auth_type: bearer
triggers:
  - rippling
  - employee
  - HR
  - department
  - group
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires RIPPLING_BASE_URL and RIPPLING_API_TOKEN environment variables.
annotations:
  readOnlyHint: false
  destructiveHint: true
  idempotentHint: false
---

# Rippling-Hr

Manage Rippling employees, departments, and groups. Use when the user mentions rippling, employee, HR, department, group.


## API Endpoints

- **GET** `/platform/api/employees` - List employees
- **GET** `/platform/api/employees/{employeeId}` - Get an employee
- **GET** `/platform/api/departments` - List departments
- **GET** `/platform/api/groups` - List groups
- **GET** `/platform/api/teams` - List teams
- **GET** `/platform/api/work_locations` - List work locations
- **GET** `/platform/api/levels` - List levels
- **GET** `/platform/api/custom_fields` - List custom fields
- **POST** `/platform/api/employees` - Create an employee
- **PUT** `/platform/api/employees/{employeeId}` - Update an employee
- **DELETE** `/platform/api/employees/{employeeId}` - Terminate an employee

## Actions

- list: List employees (GET /platform/api/employees)
- get_by_id: Get an employee (GET /platform/api/employees/{employeeId})
- list_departments: List departments (GET /platform/api/departments)
- list_groups: List groups (GET /platform/api/groups)
- list_teams: List teams (GET /platform/api/teams)
- list_work_locations: List work locations (GET /platform/api/work_locations)
- list_levels: List levels (GET /platform/api/levels)
- list_custom_fields: List custom fields (GET /platform/api/custom_fields)
- create: Create an employee (POST /platform/api/employees)
- update: Update an employee (PUT /platform/api/employees/{employeeId})
- delete: Terminate an employee (DELETE /platform/api/employees/{employeeId})

## Fields

- `filter`: object [OPTIONAL for list queries] [REQUIRED for create]
- `fields`: string [OPTIONAL] (comma-separated field names to include)

## Example Request Bodies

**List Employees with Filter:**
```json
{"filter": {"department": "Engineering"}, "fields": "name,email,department,title"}
```

**List Groups with Filter:**
```json
{"filter": {"type": "team"}, "fields": "name,members"}

## Error Responses

| Status | Meaning |
|--------|---------|
| 400 | Invalid request — missing required field, wrong type, or constraint violation |
| 401 | Authentication failed — check API credentials |
| 403 | Forbidden — insufficient permissions |
| 404 | Resource not found |
| 429 | Rate limited — retry after delay |
| 500 | Server error |
