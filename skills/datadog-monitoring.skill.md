---
name: datadog-monitoring
description: 'Manage monitors, metrics, logs, and dashboards in Datadog. Use when
  the user mentions datadog, monitor, metric, alert, dashboard, log, incident.

  '
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
annotations:
  readOnlyHint: false
  destructiveHint: false
  idempotentHint: false
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
- **GET** `/api/v2/actions-datastores` - List datastores
- **POST** `/api/v2/actions-datastores` - Create datastore
- **PUT** `/api/v2/anonymize_users` - Anonymize users

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
- list_datastores: List datastores (GET /api/v2/actions-datastores)
- create_datastore: Create datastore (POST /api/v2/actions-datastores)
- put_anonymize_users: Anonymize users (PUT /api/v2/anonymize_users)

## Fields

- `monitor_id`: string [REQUIRED for get_monitor] (monitor ID) — Monitor unique identifier
- `type`: string [REQUIRED for create_monitor] (monitor type: metric alert, service check, etc.) — Resource type
- `query`: string [REQUIRED for create_monitor, query_metrics] (monitor or metric query) — Search or filter query
- `name`: string [REQUIRED for create_monitor] (monitor name) — Display name
- `message`: string [OPTIONAL for create_monitor] (notification message) — Message text
- `from`: integer [REQUIRED for query_metrics] (start time as UNIX epoch) — From value
- `to`: integer [REQUIRED for query_metrics] (end time as UNIX epoch) — To value
- `filter`: object [OPTIONAL for search_logs] (log search filter) — Filter criteria
- `title`: string [REQUIRED for create_dashboard] (dashboard title) — Title or heading
- `widgets`: array [REQUIRED for create_dashboard] (dashboard widget definitions) — List of widgets

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

**Required fields reference:**
```json
{
  "monitor_id": "example_monitor_id",
  "title": "example_title",
  "widgets": []
}
```

## Response

**Monitor object:**
- `id`: string — Unique monitor identifier
- `name`: string — Monitor name or title
- `status`: string — Current status
- `type`: string — Monitor type or category
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
