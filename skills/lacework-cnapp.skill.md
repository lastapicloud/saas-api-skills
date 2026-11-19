---
name: lacework-cnapp
description: 'Monitor cloud security, search alerts, scan vulnerabilities, and check
  compliance via the Lacework FortiCNAPP API. Use when the user mentions lacework,
  forticnapp, cloud security posture, CNAPP, cloud compliance, lacework alert, cloud
  workload protection.

  '
version: 1.0.0
skill_type: external
base_url_env: LACEWORK_BASE_URL
auth_env_var: LACEWORK_API_TOKEN
auth_type: bearer
triggers:
  - lacework
  - forticnapp
  - cloud security posture
  - CNAPP
  - cloud compliance
  - lacework alert
  - cloud workload protection
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires LACEWORK_BASE_URL and LACEWORK_API_TOKEN environment variables.
annotations:
  readOnlyHint: false
  destructiveHint: false
  idempotentHint: false
---

# Lacework-Cnapp

Monitor cloud security, search alerts, scan vulnerabilities, and check compliance via the Lacework FortiCNAPP API. Use when the user mentions lacework, forticnapp, cloud security posture, CNAPP, cloud compliance, lacework alert, cloud workload protection.


## API Endpoints

- **GET** `/api/v2/Alerts` - List alerts
- **POST** `/api/v2/Alerts/search` - Search alerts
- **GET** `/api/v2/Alerts/{alertId}` - Get alert details
- **POST** `/api/v2/Alerts/{alertId}/close` - Close an alert
- **POST** `/api/v2/Vulnerabilities/Hosts/search` - Search host vulnerabilities
- **POST** `/api/v2/Vulnerabilities/Containers/search` - Search container vulnerabilities
- **GET** `/api/v2/Policies` - List all policies
- **GET** `/api/v2/Policies/{policyId}` - Get policy details
- **GET** `/api/v2/CloudAccounts` - List cloud account integrations
- **GET** `/api/v2/AuditLogs` - List audit logs

## Actions

- list: List alerts (GET /api/v2/Alerts)
- search: Search alerts (POST /api/v2/Alerts/search)
- get_by_id: Get alert details (GET /api/v2/Alerts/{alertId})
- create: Close an alert (POST /api/v2/Alerts/{alertId}/close)
- search_host_vulnerabilities: Search host vulnerabilities (POST /api/v2/Vulnerabilities/Hosts/search)
- search_container_vulnerabilities: Search container vulnerabilities (POST /api/v2/Vulnerabilities/Containers/search)
- list_policies: List all policies (GET /api/v2/Policies)
- get_policy_details: Get policy details (GET /api/v2/Policies/{policyId})
- list_cloud_account_integrations: List cloud account integrations (GET /api/v2/CloudAccounts)
- list_audit_logs: List audit logs (GET /api/v2/AuditLogs)

## Fields

- `alertId`: integer [REQUIRED for get_alert, close_alert] (alert ID) — Alert unique identifier
- `policyId`: string [REQUIRED for get_policy] (policy ID) — Policy unique identifier
- `filters`: array [OPTIONAL for search_alerts, search_host_vulnerabilities, search_container_vulnerabilities] (search filter objects) — List of filters
- `timeFilter`: object [OPTIONAL for search endpoints] (time range filter with startTime and endTime) — Time filter criteria
- `returns`: array [OPTIONAL for search endpoints] (fields to return in results) — List of returns

## Example Request Bodies

**Search Alerts:**
```json
{"timeFilter": {"startTime": "2024-01-01T00:00:00Z", "endTime": "2024-01-31T23:59:59Z"}, "filters": [{"field": "severity", "expression": "eq", "value": "Critical"}]}
```

**Search Host Vulnerabilities:**
```json
{"timeFilter": {"startTime": "2024-01-01T00:00:00Z", "endTime": "2024-01-31T23:59:59Z"}, "filters": [{"field": "severity", "expression": "eq", "value": "Critical"}]}
```

## Response

**Search object:**
- `id`: string — Unique search identifier
- `name`: string — Search name or title
- `status`: string — Current status
- `created_at`: string — Creation timestamp (ISO 8601)
- `updated_at`: string — Last update timestamp (ISO 8601)


**Required fields reference:**
```json
{
  "alertId": 1,
  "policyId": "example_policyId"
}
```


**Required fields reference:**
```json
{
  "alertId": 1,
  "policyId": "example_policyId"
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
