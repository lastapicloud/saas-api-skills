---
name: stackhawk-dast
description: 'Manage StackHawk DAST scans and findings. Use when the user mentions
  stackhawk, DAST, scan, finding, vulnerability, dynamic analysis.

  '
version: 1.0.0
skill_type: external
base_url_env: STACKHAWK_BASE_URL
auth_env_var: STACKHAWK_API_KEY
auth_type: bearer
triggers:
  - stackhawk
  - DAST
  - scan
  - finding
  - vulnerability
  - dynamic analysis
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires STACKHAWK_BASE_URL and STACKHAWK_API_KEY environment variables.
annotations:
  readOnlyHint: false
  destructiveHint: false
  idempotentHint: false
---

# Stackhawk-Dast

Manage StackHawk DAST scans and findings. Use when the user mentions stackhawk, DAST, scan, finding, vulnerability, dynamic analysis.


## API Endpoints

- **GET** `/api/v1/org/{orgId}/app` - List applications
- **GET** `/api/v1/org/{orgId}/app/{appId}` - Get an application
- **POST** `/api/v1/org/{orgId}/app` - Create an application
- **GET** `/api/v1/org/{orgId}/app/{appId}/scan` - List scans
- **GET** `/api/v1/org/{orgId}/app/{appId}/scan/{scanId}` - Get a scan
- **GET** `/api/v1/org/{orgId}/app/{appId}/scan/{scanId}/alerts` - List alerts for a scan
- **PATCH** `/api/v1/org/{orgId}/app/{appId}/alert/{alertId}/triage` - Triage an alert
- **GET** `/api/v1/org/{orgId}/env` - List environments

## Actions

- list: List applications (GET /api/v1/org/{orgId}/app)
- get_by_id: Get an application (GET /api/v1/org/{orgId}/app/{appId})
- create: Create an application (POST /api/v1/org/{orgId}/app)
- list_scans: List scans (GET /api/v1/org/{orgId}/app/{appId}/scan)
- get_scan: Get a scan (GET /api/v1/org/{orgId}/app/{appId}/scan/{scanId})
- list_alerts_scan: List alerts for a scan (GET /api/v1/org/{orgId}/app/{appId}/scan/{scanId}/alerts)
- patch_triage: Triage an alert (PATCH /api/v1/org/{orgId}/app/{appId}/alert/{alertId}/triage)
- list_environments: List environments (GET /api/v1/org/{orgId}/env)

## Fields

- `name`: string [REQUIRED for create app] — Display name
- `env`: string [REQUIRED for create app] — Env
- `dataType`: string [REQUIRED for create app] — Data resource type
- `status`: string [REQUIRED for triage] (e.g., "ACCEPTED_RISK", "FALSE_POSITIVE", "FIXED") — Current status

## Example Request Bodies

**Create Application:**
```json
{"name": "My Web App", "env": "production", "dataType": "WEB"}
```

**Triage Alert:**
```json
{"status": "FALSE_POSITIVE"}

## Response

**App object:**
- `id`: string — Unique app identifier
- `name`: string — App name or title
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
