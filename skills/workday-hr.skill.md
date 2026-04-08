---
name: workday-hr
description: Manage workers and organizations via Workday. Use when the user mentions
  workday, hr, worker, employee, organization, payroll.
version: 1.0.0
skill_type: external
base_url_env: WORKDAY_BASE_URL
auth_env_var: WORKDAY_ACCESS_TOKEN
auth_type: bearer
triggers:
  - workday
  - hr
  - worker
  - employee
  - organization
  - payroll
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires WORKDAY_BASE_URL and WORKDAY_ACCESS_TOKEN environment variables.
---

# Workday-Hr

Manage workers and organizations via Workday. Use when the user mentions workday, hr, worker, employee, organization, payroll.

## API Endpoints

- **GET** `/ccx/api/v1/{tenant}/workers` - List workers
- **GET** `/ccx/api/v1/{tenant}/workers/{id}` - Get worker
- **GET** `/ccx/api/v1/{tenant}/organizations` - List organizations
- **GET** `/ccx/api/v1/{tenant}/organizationTypes` - List organization types
- **GET** `/ccx/api/v1/{tenant}/locations` - List locations
- **GET** `/ccx/api/v1/{tenant}/supervisoryOrganizations` - List supervisory orgs
- **POST** `/ccx/api/v1/{tenant}/workers` - Create worker
- **PUT** `/ccx/api/v1/{tenant}/workers/{id}` - Update worker

## Actions

- list: List workers (GET /ccx/api/v1/{tenant}/workers)
- get_by_id: Get worker (GET /ccx/api/v1/{tenant}/workers/{id})
- list_organizations: List organizations (GET /ccx/api/v1/{tenant}/organizations)
- list_organizationtypes: List organization types (GET /ccx/api/v1/{tenant}/organizationTypes)
- list_locations: List locations (GET /ccx/api/v1/{tenant}/locations)
- list_supervisoryorganizations: List supervisory orgs (GET /ccx/api/v1/{tenant}/supervisoryOrganizations)
- create: Create worker (POST /ccx/api/v1/{tenant}/workers)
- update: Update worker (PUT /ccx/api/v1/{tenant}/workers/{id})

## Fields

- `tenant`: string [REQUIRED]
- `limit`: integer [OPTIONAL]
- `offset`: integer [OPTIONAL]

## Example Request Bodies

**Create Worker:**
```json
{"tenant": "mycompany", "firstName": "Jane", "lastName": "Smith", "email": "jane.smith@company.com"}
```

**List Workers (query parameters):**
```json
{"tenant": "mycompany", "limit": 50, "offset": 0}
