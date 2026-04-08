---
name: datadog-monitoring
description: Manage monitors, metrics, logs, and dashboards in Datadog. Use when the
  user mentions datadog, monitor, metric, alert, dashboard, log, incident.
version: 1.0.0
skill_type: external
base_url_env: DATADOG_BASE_URL
auth_env_var: DATADOG_API_KEY
auth_type: header
triggers:
  - datadog
  - monitor
  - metric
  - alert
  - dashboard
  - log
  - incident
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires DATADOG_BASE_URL and DATADOG_API_KEY environment variables.
---

# Datadog-Monitoring

Manage monitors, metrics, logs, and dashboards in Datadog. Use when the user mentions datadog, monitor, metric, alert, dashboard, log, incident.

## API Endpoints

- **GET** `/api/v1/monitor` - List monitors
- **POST** `/api/v1/monitor` - Create a monitor
- **GET** `/api/v1/monitor/{monitor_id}` - Get a monitor
- **GET** `/api/v1/query` - Query metrics
- **POST** `/api/v2/logs/events/search` - Search logs
- **GET** `/api/v2/incidents` - List incidents
- **POST** `/api/v1/dashboard` - Create a dashboard
- **GET** `/oauth2/v1/authorize`
- **POST** `/oauth2/v1/authorize`
- **POST** `/oauth2/v1/token`
- **POST** `/oauth2/v1/revoke`
- **POST** `/api/v2/api_keys/marketplace`

## Actions

- list: List monitors (GET /api/v1/monitor)
- create: Create a monitor (POST /api/v1/monitor)
- get_by_id: Get a monitor (GET /api/v1/monitor/{monitor_id})
- query: Query metrics (GET /api/v1/query)
- search: Search logs (POST /api/v2/logs/events/search)
- list_incidents: List incidents (GET /api/v2/incidents)
- create_dashboard: Create a dashboard (POST /api/v1/dashboard)
- list_authorize: GET /oauth2/v1/authorize (GET /oauth2/v1/authorize)
- create_authorize: POST /oauth2/v1/authorize (POST /oauth2/v1/authorize)
- create_token: POST /oauth2/v1/token (POST /oauth2/v1/token)
- create_revoke: POST /oauth2/v1/revoke (POST /oauth2/v1/revoke)
- create_marketplace: POST /api/v2/api_keys/marketplace (POST /api/v2/api_keys/marketplace)

## Fields

- `monitor_id`: string [REQUIRED for get_monitor] (monitor ID)
- `type`: string [REQUIRED for create_monitor] (monitor type: metric alert, service check, etc.)
- `query`: string [REQUIRED for create_monitor, query_metrics] (monitor or metric query)
- `name`: string [REQUIRED for create_monitor] (monitor name)
- `message`: string [OPTIONAL for create_monitor] (notification message)
- `from`: integer [REQUIRED for query_metrics] (start time as UNIX epoch)
- `to`: integer [REQUIRED for query_metrics] (end time as UNIX epoch)
- `filter`: object [OPTIONAL for search_logs] (log search filter)
- `title`: string [REQUIRED for create_dashboard] (dashboard title)
- `widgets`: array [REQUIRED for create_dashboard] (dashboard widget definitions)

## Example Request Bodies

**Create Monitor:**
```json
{"type": "metric alert", "query": "avg(last_5m):avg:system.cpu.user{*} > 90", "name": "High CPU Usage", "message": "CPU usage is above 90%"}
```

**Search Logs:**
```json
{"filter": {"query": "service:web-app status:error", "from": "now-1h", "to": "now"}, "page": {"limit": 50}}
```

**Query Metrics (Query Params):**
Query parameter: `from=1679000000&to=1679100000&query=avg:system.cpu.user{*}`
