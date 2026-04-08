---
name: stackhawk-dast
description: Manage StackHawk DAST scans and findings. Use when the user mentions
  stackhawk, DAST, scan, finding, vulnerability, dynamic analysis.
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
- list_scan: List scans (GET /api/v1/org/{orgId}/app/{appId}/scan)
- get_by_id_scan: Get a scan (GET /api/v1/org/{orgId}/app/{appId}/scan/{scanId})
- list_alerts: List alerts for a scan (GET /api/v1/org/{orgId}/app/{appId}/scan/{scanId}/alerts)
- patch_triage: Triage an alert (PATCH /api/v1/org/{orgId}/app/{appId}/alert/{alertId}/triage)
- list_env: List environments (GET /api/v1/org/{orgId}/env)

## Fields

- `name`: string [REQUIRED for create app]
- `env`: string [REQUIRED for create app]
- `dataType`: string [REQUIRED for create app]
- `status`: string [REQUIRED for triage] (e.g., "ACCEPTED_RISK", "FALSE_POSITIVE", "FIXED")

## Example Request Bodies

**Create Application:**
```json
{"name": "My Web App", "env": "production", "dataType": "WEB"}
```

**Triage Alert:**
```json
{"status": "FALSE_POSITIVE"}
