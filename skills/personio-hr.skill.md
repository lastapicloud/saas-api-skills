---
name: personio-hr
description: Manage employees and attendance via Personio (API 1.0). Use when the
  user mentions personio, hr, employee, attendance, absence, time off.
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
- list_time_off_types: Provides a list of available time-off types, for example 'Paid vacation', 'Paren (GET /company/time-off-types)
- list_time_offs: This endpoint is responsible for fetching absence data for the company employees (GET /company/time-offs)
- create_attendances: This endpoint is responsible for adding attendance data for the company employee (POST /company/attendances)
- create_employees: Create an employee (POST /company/employees)
- create_time_offs: This endpoint is responsible for adding absence data for the company employees. (POST /company/time-offs)
- update: This endpoint is responsible for updating attendance data for the company employ (PATCH /company/attendances/{id})
- get_by_id: Show employee by ID (GET /company/employees/{employee_id})
- get_by_id_time_offs: Absence Period (GET /company/time-offs/{id})
- delete: This endpoint is responsible for deleting attendance data for the company employ (DELETE /company/attendances/{id})
- delete_time_offs: This endpoint is responsible for deleting absence period data for the company em (DELETE /company/time-offs/{id})
- get_by_id_profile_picture: Show employee profile picture (GET /company/employees/{employee_id}/profile-picture/{width})

## Fields

### Employee
- `first_name`: string [REQUIRED] - Employee first name
- `last_name`: string [REQUIRED] - Employee last name
- `email`: string [REQUIRED] - Employee email address
- `department`: string [OPTIONAL] - Department name or ID
- `position`: string [OPTIONAL] - Job position
- `hire_date`: date [OPTIONAL] - Start date (YYYY-MM-DD)

### Attendance
- `employee`: integer [REQUIRED] - Employee ID
- `date`: date [REQUIRED] - Attendance date (YYYY-MM-DD)
- `start_time`: string [REQUIRED] - Start time (HH:MM)
- `end_time`: string [REQUIRED] - End time (HH:MM)
- `break`: integer [OPTIONAL] - Break duration in minutes
- `notes`: string [OPTIONAL] - Additional notes

### Time Off
- `employee`: integer [REQUIRED] - Employee ID
- `start_date`: date [REQUIRED] - Start date (YYYY-MM-DD)
- `end_date`: date [REQUIRED] - End date (YYYY-MM-DD)
- `time_off_type`: integer [REQUIRED] - Time-off type ID
- `status`: string [OPTIONAL] - approved, pending

## Example Request Bodies

**Create Employee:**
```json
{"employee": {"first_name": "Maria", "last_name": "Garcia", "email": "maria.garcia@company.com", "department": "Engineering"}}
```

**Create Attendance:**
```json
{"attendances": [{"employee": 12345, "date": "2024-03-15", "start_time": "09:00", "end_time": "17:00", "break": 60}]}
```
