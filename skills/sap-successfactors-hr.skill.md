---
name: sap-successfactors-hr
description: Manage employees and HR data via SAP SuccessFactors. Use when the user
  mentions sap, successfactors, hr, employee, performance, learning.
version: 1.0.0
skill_type: external
base_url_env: SAP_SUCCESSFACTORS_BASE_URL
auth_env_var: SAP_SUCCESSFACTORS_API_TOKEN
auth_type: bearer
triggers:
  - sap
  - successfactors
  - hr
  - employee
  - performance
  - learning
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires SAP_SUCCESSFACTORS_BASE_URL and SAP_SUCCESSFACTORS_API_TOKEN
  environment variables.
---

# Sap-Successfactors-Hr

Manage employees and HR data via SAP SuccessFactors. Use when the user mentions sap, successfactors, hr, employee, performance, learning.

## API Endpoints

- **GET** `/odata/v2/User` - List users
- **GET** `/odata/v2/User/{userId}` - Get user
- **GET** `/odata/v2/EmpEmployment` - List employments
- **GET** `/odata/v2/PerPersonal` - List personal info
- **GET** `/odata/v2/EmpJob` - List job info
- **GET** `/odata/v2/EmpCompensation` - List compensation
- **GET** `/odata/v2/TimeOff` - List time off
- **POST** `/odata/v2/TimeOff` - Create time off
- **PUT** `/odata/v2/User/{userId}` - Update user

## Actions

- list: List users (GET /odata/v2/User)
- get_by_id: Get user (GET /odata/v2/User/{userId})
- list_empemployment: List employments (GET /odata/v2/EmpEmployment)
- list_perpersonal: List personal info (GET /odata/v2/PerPersonal)
- list_empjob: List job info (GET /odata/v2/EmpJob)
- list_empcompensation: List compensation (GET /odata/v2/EmpCompensation)
- list_timeoff: List time off (GET /odata/v2/TimeOff)
- create: Create time off (POST /odata/v2/TimeOff)
- update: Update user (PUT /odata/v2/User/{userId})

## Fields

- `$filter`: string [OPTIONAL]
- `$select`: string [OPTIONAL]
- `$top`: integer [OPTIONAL]

## Example Request Bodies

**Create Time Off:**
```json
{"userId": "EMP001", "timeType": "VACATION", "startDate": "2026-04-01", "endDate": "2026-04-05"}
```

**List Users with Filter:**
```json
{"$filter": "department eq 'Engineering'", "$select": "userId,firstName,lastName", "$top": 50}
