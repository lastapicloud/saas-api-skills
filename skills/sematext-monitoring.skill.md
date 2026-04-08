---
name: sematext-monitoring
description: Manage monitors and alerts via Sematext. Use when the user mentions sematext,
  monitoring, logs, metrics, alert, observability.
version: 1.0.0
skill_type: external
base_url_env: SEMATEXT_BASE_URL
auth_env_var: SEMATEXT_API_TOKEN
auth_type: header
triggers:
  - sematext
  - monitoring
  - logs
  - metrics
  - alert
  - observability
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires SEMATEXT_BASE_URL and SEMATEXT_API_TOKEN environment variables.
---

# Sematext-Monitoring

Manage monitors and alerts via Sematext. Use when the user mentions sematext, monitoring, logs, metrics, alert, observability.

## API Endpoints

- **GET** `/spm-reports/api/v3/apps` - List apps
- **POST** `/spm-reports/api/v3/apps` - Create app
- **GET** `/spm-reports/api/v3/apps/{appId}` - Get app
- **DELETE** `/spm-reports/api/v3/apps/{appId}` - Delete app
- **GET** `/spm-reports/api/v3/apps/{appId}/alerts` - List alerts
- **POST** `/spm-reports/api/v3/apps/{appId}/alerts` - Create alert
- **GET** `/logsene-reports/api/v3/apps/{appId}/search` - Search logs

## Actions

- list: List apps (GET /spm-reports/api/v3/apps)
- create: Create app (POST /spm-reports/api/v3/apps)
- get_by_id: Get app (GET /spm-reports/api/v3/apps/{appId})
- delete: Delete app (DELETE /spm-reports/api/v3/apps/{appId})
- list_alerts: List alerts (GET /spm-reports/api/v3/apps/{appId}/alerts)
- create_alerts: Create alert (POST /spm-reports/api/v3/apps/{appId}/alerts)
- search: Search logs (GET /logsene-reports/api/v3/apps/{appId}/search)

## Fields

- `name`: string [REQUIRED for create]
- `appType`: string [REQUIRED for create]

## Example Request Bodies

**Create App:**
```json
{"name": "production-api-monitor", "appType": "Logsene"}
```

**Create Alert:**
```json
{"name": "High Error Rate", "query": "severity:error", "threshold": 100}
```
