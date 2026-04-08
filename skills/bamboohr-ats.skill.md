---
name: bamboohr-ats
description: Manage employees, applicants, and job openings in BambooHR. Use when
  the user mentions bamboohr, bamboo hr, bamboohr employee, bamboohr applicant, bamboohr
  job opening.
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
- get_by_id_applications: Get an application (GET /api/gateway.php/{companyDomain}/v1/applicant_tracking/applications/{id})
- create_status: Change application status (POST /api/gateway.php/{companyDomain}/v1/applicant_tracking/applications/{id}/status)
- list_job_openings: List job openings (GET /api/gateway.php/{companyDomain}/v1/applicant_tracking/job_openings)
- list_statuses: List application statuses (GET /api/gateway.php/{companyDomain}/v1/applicant_tracking/statuses)
- delete: Delete an employee (DELETE /api/gateway.php/{companyDomain}/v1/employees/{id})
- delete_applications: Delete an application (DELETE /api/gateway.php/{companyDomain}/v1/applicant_tracking/applications/{id})

## Fields

- `id`: integer [REQUIRED for get_employee, update_employee, get_application, change_application_status] (record ID)
- `companyDomain`: string [REQUIRED] (company subdomain)
- `firstName`: string [REQUIRED for create_employee] (first name)
- `lastName`: string [REQUIRED for create_employee] (last name)
- `emailAddress`: string [OPTIONAL] (email address)
- `jobTitle`: string [OPTIONAL] (job title)
- `department`: string [OPTIONAL] (department)
- `status`: integer [REQUIRED for change_application_status] (new status ID)

## Example Request Bodies

**Create Employee:**
```json
{"firstName": "Jane", "lastName": "Doe", "emailAddress": "jane@example.com", "jobTitle": "Senior Engineer"}
```

**Change Application Status:**
```json
{"status": 2}
```
