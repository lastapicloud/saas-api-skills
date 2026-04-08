---
name: adp-hris
description: Manage ADP workers and HR data. Use when the user mentions adp, worker,
  HR, payroll, employee.
version: 1.0.0
skill_type: external
base_url_env: ADP_BASE_URL
auth_env_var: ADP_ACCESS_TOKEN
auth_type: bearer
triggers:
  - adp
  - worker
  - HR
  - payroll
  - employee
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires ADP_BASE_URL and ADP_ACCESS_TOKEN environment variables.
---

# Adp-Hris

Manage ADP workers and HR data. Use when the user mentions adp, worker, HR, payroll, employee.

## API Endpoints

- **GET** `/hr/v2/workers` - List workers
- **GET** `/hr/v2/workers/{aoid}` - Get a worker
- **POST** `/events/hr/v1/worker.hire` - Hire a worker
- **POST** `/events/hr/v1/worker.terminate` - Terminate a worker
- **GET** `/hr/v2/workers/{aoid}/work-assignments` - Get work assignments
- **GET** `/payroll/v1/workers/{aoid}/pay-distributions` - Get pay distributions
- **GET** `/core/v1/organization-departments` - List departments
- **GET** `/hr/v2/worker-demographics` - Get worker demographics

## Actions

- list: List workers (GET /hr/v2/workers)
- get_by_id: Get a worker (GET /hr/v2/workers/{aoid})
- create: Hire a worker (POST /events/hr/v1/worker.hire)
- create_worker_terminate: Terminate a worker (POST /events/hr/v1/worker.terminate)
- list_work_assignments: Get work assignments (GET /hr/v2/workers/{aoid}/work-assignments)
- list_pay_distributions: Get pay distributions (GET /payroll/v1/workers/{aoid}/pay-distributions)
- list_organization_departments: List departments (GET /core/v1/organization-departments)
- list_worker_demographics: Get worker demographics (GET /hr/v2/worker-demographics)

## Fields

- `events`: array [REQUIRED for hire/terminate]
- `data`: object [REQUIRED] with worker details
- `effectiveDateTime`: string [REQUIRED for events]

## Example Request Bodies

**Hire Worker:**
```json
{"events": [{"data": {"transform": {"worker": {"person": {"legalName": {"givenName": "Maria", "familyName": "Garcia"}}}}}, "effectiveDateTime": "2026-04-01T00:00:00Z"}]}
```

**Terminate Worker:**
```json
{"events": [{"data": {"transform": {"worker": {"workerStatus": {"reasonCode": "Resignation"}}}}, "effectiveDateTime": "2026-05-15T00:00:00Z"}]}
```
