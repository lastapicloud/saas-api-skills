---
name: adp-hris
description: 'Manage ADP workers and HR data. Use when the user mentions adp, worker,
  HR, payroll, employee.

  '
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
annotations:
  readOnlyHint: false
  destructiveHint: false
  idempotentHint: false
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
- create_terminate_worker: Terminate a worker (POST /events/hr/v1/worker.terminate)
- get_work_assignments: Get work assignments (GET /hr/v2/workers/{aoid}/work-assignments)
- get_pay_distributions: Get pay distributions (GET /payroll/v1/workers/{aoid}/pay-distributions)
- list_departments: List departments (GET /core/v1/organization-departments)
- get_worker_demographics: Get worker demographics (GET /hr/v2/worker-demographics)

## Fields

- `events`: array [REQUIRED for hire/terminate] — List of events
- `data`: object [REQUIRED] with worker details — Request payload data
- `effectiveDateTime`: string [REQUIRED for events] — Effectivedatetime

## Example Request Bodies

**Hire Worker:**
```json
{"events": [{"data": {"transform": {"worker": {"person": {"legalName": {"givenName": "Maria", "familyName": "Garcia"}}}}}, "effectiveDateTime": "2026-04-01T00:00:00Z"}]}
```

**Terminate Worker:**
```json
{"events": [{"data": {"transform": {"worker": {"workerStatus": {"reasonCode": "Resignation"}}}}, "effectiveDateTime": "2026-05-15T00:00:00Z"}]}
```

## Response

**Worker object:**
- `id`: string — Unique worker identifier
- `name`: string — Worker name or title
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
