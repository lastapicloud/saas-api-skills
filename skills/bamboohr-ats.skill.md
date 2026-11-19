---
name: bamboohr-ats
description: 'Manage employees, applicants, and job openings in BambooHR. Use when
  the user mentions bamboohr, bamboo hr, bamboohr employee, bamboohr applicant, bamboohr
  job opening.

  '
version: 1.0.0
skill_type: external
base_url_env: BAMBOOHR_BASE_URL
auth_env_var: BAMBOOHR_API_KEY
auth_type: basic
triggers:
  - bamboohr
  - bamboo hr
  - bamboohr employee
  - bamboohr applicant
  - bamboohr job opening
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires BAMBOOHR_BASE_URL and BAMBOOHR_API_KEY environment variables.
annotations:
  readOnlyHint: false
  destructiveHint: true
  idempotentHint: false
---

# Bamboohr-Ats

Manage employees, applicants, and job openings in BambooHR. Use when the user mentions bamboohr, bamboo hr, bamboohr employee, bamboohr applicant, bamboohr job opening.


## API Endpoints

- **GET** `/api/gateway.php/{companyDomain}/v1/employees/directory` - List employees directory
- **GET** `/api/gateway.php/{companyDomain}/v1/employees/{id}` - Get an employee by ID
- **POST** `/api/gateway.php/{companyDomain}/v1/employees` - Create an employee
- **PUT** `/api/gateway.php/{companyDomain}/v1/employees/{id}` - Update an employee
- **GET** `/api/gateway.php/{companyDomain}/v1/applicant_tracking/applications` - List applications
- **GET** `/api/gateway.php/{companyDomain}/v1/applicant_tracking/applications/{id}` - Get an application
- **POST** `/api/gateway.php/{companyDomain}/v1/applicant_tracking/applications/{id}/status` - Change application status
- **GET** `/api/gateway.php/{companyDomain}/v1/applicant_tracking/job_openings` - List job openings
- **GET** `/api/gateway.php/{companyDomain}/v1/applicant_tracking/statuses` - List application statuses
- **DELETE** `/api/gateway.php/{companyDomain}/v1/employees/{id}` - Delete an employee
- **DELETE** `/api/gateway.php/{companyDomain}/v1/applicant_tracking/applications/{id}` - Delete an application

## Actions

- list: List employees directory (GET /api/gateway.php/{companyDomain}/v1/employees/directory)
- get_by_id: Get an employee by ID (GET /api/gateway.php/{companyDomain}/v1/employees/{id})
- create: Create an employee (POST /api/gateway.php/{companyDomain}/v1/employees)
- update: Update an employee (PUT /api/gateway.php/{companyDomain}/v1/employees/{id})
- list_applications: List applications (GET /api/gateway.php/{companyDomain}/v1/applicant_tracking/applications)
- get_application: Get an application (GET /api/gateway.php/{companyDomain}/v1/applicant_tracking/applications/{id})
- create_change_application_status: Change application status (POST /api/gateway.php/{companyDomain}/v1/applicant_tracking/applications/{id}/status)
- list_job_openings: List job openings (GET /api/gateway.php/{companyDomain}/v1/applicant_tracking/job_openings)
- list_application_statuses: List application statuses (GET /api/gateway.php/{companyDomain}/v1/applicant_tracking/statuses)
- delete: Delete an employee (DELETE /api/gateway.php/{companyDomain}/v1/employees/{id})
- delete_application: Delete an application (DELETE /api/gateway.php/{companyDomain}/v1/applicant_tracking/applications/{id})

## Fields

- `id`: integer [REQUIRED for get_employee, update_employee, get_application, change_application_status] (record ID) — Unique identifier
- `companyDomain`: string [REQUIRED] (company subdomain) — Companydomain
- `firstName`: string [REQUIRED for create_employee] (first name) — First display name
- `lastName`: string [REQUIRED for create_employee] (last name) — Last display name
- `emailAddress`: string [OPTIONAL] (email address) — Email physical or postal address
- `jobTitle`: string [OPTIONAL] (job title) — Job title or heading
- `department`: string [OPTIONAL] (department) — Department
- `status`: integer [REQUIRED for change_application_status] (new status ID) — Current status

## Example Request Bodies

**Create Employee:**
```json
{"firstName": "Jane", "lastName": "Doe", "emailAddress": "jane@example.com", "jobTitle": "Senior Engineer"}
```

**Change Application Status:**
```json
{"status": 2}
```

## Response

**Employee object:**
- `id`: string — Unique employee identifier
- `name`: string — Employee name or title
- `status`: string — Current status
- `created_at`: string — Creation timestamp (ISO 8601)
- `updated_at`: string — Last update timestamp (ISO 8601)


**Required fields reference:**
```json
{
  "id": 1,
  "companyDomain": "example_companyDomain"
}
```


**Required fields reference:**
```json
{
  "id": 1,
  "companyDomain": "example_companyDomain"
}
```

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
