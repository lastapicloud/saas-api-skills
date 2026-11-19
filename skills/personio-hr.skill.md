---
name: personio-hr
description: 'Manage employees and attendance via Personio (API 1.0). Use when the
  user mentions personio, hr, employee, attendance, absence, time off.

  '
version: 1.0.0
skill_type: external
base_url_env: PERSONIO_BASE_URL
auth_env_var: PERSONIO_API_TOKEN
auth_type: bearer
triggers:
  - personio
  - hr
  - employee
  - attendance
  - absence
  - time off
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires PERSONIO_BASE_URL and PERSONIO_API_TOKEN environment variables.
annotations:
  readOnlyHint: false
  destructiveHint: true
  idempotentHint: false
---

# Personio-Hr

Manage employees and attendance via Personio (API 1.0). Use when the user mentions personio, hr, employee, attendance, absence, time off.


## API Endpoints

- **POST** `/auth` - Request Authentication Token
- **GET** `/company/attendances` - This endpoint is responsible for fetching attendance data for the company employees. It is possible to paginate
- **GET** `/company/employees` - List Employees
- **GET** `/company/time-off-types` - Provides a list of available time-off types, for example 'Paid vacation', 'Parental leave' or 'Home office'
- **GET** `/company/time-offs` - This endpoint is responsible for fetching absence data for the company employees. It is possible to paginate results,
- **POST** `/company/attendances` - This endpoint is responsible for adding attendance data for the company employees. It is possible to add attendances
- **POST** `/company/employees` - Create an employee
- **POST** `/company/time-offs` - This endpoint is responsible for adding absence data for the company employees.
- **PATCH** `/company/attendances/{id}` - This endpoint is responsible for updating attendance data for the company employees. Attributes are not required and if
- **GET** `/company/employees/{employee_id}` - Show employee by ID
- **GET** `/company/time-offs/{id}` - Absence Period
- **DELETE** `/company/attendances/{id}` - This endpoint is responsible for deleting attendance data for the company employees.
- **DELETE** `/company/time-offs/{id}` - This endpoint is responsible for deleting absence period data for the company employees.
- **GET** `/company/employees/{employee_id}/profile-picture/{width}` - Show employee profile picture

## Actions

- create: Request Authentication Token (POST /auth)
- list: This endpoint is responsible for fetching attendance data for the company employ (GET /company/attendances)
- list_employees: List Employees (GET /company/employees)
- get_provides_list_available_timeoff: Provides a list of available time-off types, for example 'Paid vacation', 'Paren (GET /company/time-off-types)
- get_this_endpoint_is_responsible: This endpoint is responsible for fetching absence data for the company employees (GET /company/time-offs)
- create_this_endpoint_is_responsible: This endpoint is responsible for adding attendance data for the company employee (POST /company/attendances)
- create_employee: Create an employee (POST /company/employees)
- create_time_offs: This endpoint is responsible for adding absence data for the company employees. (POST /company/time-offs)
- update: This endpoint is responsible for updating attendance data for the company employ (PATCH /company/attendances/{id})
- get_by_id: Show employee by ID (GET /company/employees/{employee_id})
- get_absence_period: Absence Period (GET /company/time-offs/{id})
- delete: This endpoint is responsible for deleting attendance data for the company employ (DELETE /company/attendances/{id})
- delete_this_endpoint_is_responsible: This endpoint is responsible for deleting absence period data for the company em (DELETE /company/time-offs/{id})
- get_show_employee_profile_picture: Show employee profile picture (GET /company/employees/{employee_id}/profile-picture/{width})

## Fields

### Attendances (This endpoint is responsible for adding attendance data for )
- `attendances`: array [OPTIONAL] — List of attendances

### Employees (Create an employee)
- `employee[department]`: string [OPTIONAL] — Employee department
- `employee[email]`: string [REQUIRED] — Employee email
- `employee[first_name]`: string [REQUIRED] — Employee first name
- `employee[gender]`: string [OPTIONAL] (enum: male, female, diverse) — Employee gender
- `employee[hire_date]`: string [OPTIONAL] (format: date) — Employee hire date
- `employee[last_name]`: string [REQUIRED] — Employee last name
- `employee[position]`: string [OPTIONAL] — Employee position
- `employee[weekly_hours]`: number [OPTIONAL] — Employee weekly working hours

### Time Offs (This endpoint is responsible for adding absence data for the)
- `comment`: string [OPTIONAL] — Optional comment
- `employee_id`: integer [REQUIRED] — Employee identifier
- `end_date`: string [REQUIRED] (format: date) — Absence end date as YYYY-MM-DD
- `half_day_end`: boolean [REQUIRED] — Weather the end date is a half-day off
- `half_day_start`: boolean [REQUIRED] — Weather the start date is a half-day off
- `start_date`: string [REQUIRED] (format: date) — Absence start date as YYYY-MM-DD
- `time_off_type_id`: integer [REQUIRED] — Time-off type identifier

## Example Request Bodies

**Create Employee:**
```json
{"employee": {"first_name": "Maria", "last_name": "Garcia", "email": "maria.garcia@company.com", "department": "Engineering"}}
```

**Create Attendance:**
```json
{"attendances": [{"employee": 12345, "date": "2024-03-15", "start_time": "09:00", "end_time": "17:00", "break": 60}]}
```

**Required fields reference:**
```json
{
  "employee_id": 1,
  "end_date": "example_end_date",
  "half_day_end": true,
  "half_day_start": true,
  "start_date": "example_start_date",
  "time_off_type_id": 1
}
```

## Response

**Attendance object:**
- `id`: string — Unique attendance identifier
- `name`: string — Attendance name or title
- `status`: string — Current status
- `type`: string — Attendance type or category
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
