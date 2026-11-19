---
name: openobserve-logs
description: Log management and analytics via OpenObserve. Use when the user mentions openobserve, log management, log analytics, observability, Loki alternative.
version: 1.0.0
skill_type: external
base_url_env: OPENOBSERVE_BASE_URL
auth_env_var: OPENOBSERVE_API_KEY
auth_type: basic
triggers:
  - openobserve
  - log management
  - log analytics
  - observability
  - Loki alternative
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
  documentation: https://openobserve.ai/docs/api/
---

# Openobserve-Logs

Log management and analytics via OpenObserve. Use when the user mentions openobserve, log management, log analytics, observability, Loki alternative.

## API Endpoints

- **POST** `/api/{organization}/_json` - Ingest logs
- **POST** `/api/{organization}/_bulk` - Bulk ingest
- **GET** `/api/{organization}/{stream}/_search` - Search logs
- **GET** `/api/{organization}/{stream}/_values` - Get field values
- **POST** `/api/{organization}/{stream}/_delete` - Delete old logs
- **GET** `/api/{organization}/dashboards` - List dashboards
- **GET** `/api/{organization}/alerts` - List alerts
- **POST** `/api/{organization}/alerts` - Create alert

## Actions

- ingest_logs: Ingest logs (POST /api/{organization}/_json)
- bulk_ingest: Bulk ingest (POST /api/{organization}/_bulk)
- search_logs: Search logs (GET /api/{organization}/{stream}/_search)
- get_values: Get field values (GET /api/{organization}/{stream}/_values)
- delete_logs: Delete old logs (POST /api/{organization}/{stream}/_delete)
- list_dashboards: List dashboards (GET /api/{organization}/dashboards)
- list_alerts: List alerts (GET /api/{organization}/alerts)
- create_alert: Create alert (POST /api/{organization}/alerts)

## Fields

- `organization`: string [REQUIRED] - Organization name
- `stream`: string [REQUIRED] - Stream/log stream name
- `records`: array [REQUIRED for ingest] - Log records
- `query`: string [REQUIRED for search] - Search query
- `startTime`: integer [REQUIRED for search] - Start timestamp
- `endTime`: integer [REQUIRED for search] - End timestamp

## Example Request Bodies

**Ingest Logs:**
```json
{"records": [{"timestamp": 1704067200, "message": "User logged in", "level": "info"}]}
```

**Search Logs:**
```json
{"query": "level:error", "startTime": 1704067200, "endTime": 1704153600, "size": 100}
```
