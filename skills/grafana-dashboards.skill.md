---
name: grafana-dashboards
description: Manage dashboards, alerts, and datasources via the Grafana HTTP API.
  Use when the user mentions grafana, dashboard, alert, monitor, metric, panel.
version: 1.0.0
skill_type: external
base_url_env: GRAFANA_BASE_URL
auth_env_var: GRAFANA_API_TOKEN
auth_type: bearer
triggers:
  - grafana
  - dashboard
  - alert
  - monitor
  - metric
  - panel
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires GRAFANA_BASE_URL and GRAFANA_API_TOKEN environment variables.
---

# Grafana-Dashboards

Manage dashboards, alerts, and datasources via the Grafana HTTP API. Use when the user mentions grafana, dashboard, alert, monitor, metric, panel.

## API Endpoints

- **GET** `/api/search` - List dashboards
- **POST** `/api/dashboards/db` - Create or update a dashboard
- **GET** `/api/dashboards/uid/{uid}` - Get dashboard by UID
- **DELETE** `/api/dashboards/uid/{uid}` - Delete dashboard by UID
- **GET** `/api/v1/provisioning/alert-rules` - List alert rules
- **POST** `/api/v1/provisioning/alert-rules` - Create an alert rule
- **GET** `/api/datasources` - List datasources
- **POST** `/apis/dashboard.grafana.app/v1beta1/namespaces/:namespace/dashboards` - Creates a new dashboard.
- **POST** `/apis/dashboard.grafana.app/v1beta1/namespaces/default/dashboards`
- **PUT** `/apis/dashboard.grafana.app/v1beta1/namespaces/:namespace/dashboards/:uid` - Updates an existing dashboard via the dashboard uid.
- **POST** `/apis/dashboard.grafana.app/v1beta1/namespaces/default/dashboards/gdxccn`
- **GET** `/apis/dashboard.grafana.app/v1beta1/namespaces/:namespace/dashboards/:uid` - Gets a dashboard via the dashboard uid.
- **GET** `/apis/dashboard.grafana.app/v1beta1/namespaces/default/dashboards/gdxccn` - Example Response:
- **GET** `/apis/dashboard.grafana.app/v1beta1/namespaces/:namespace/dashboards/:uid/dto` - Retrieves a dashboard with additional access information.
- **GET** `/apis/dashboard.grafana.app/v1beta1/namespaces/:namespace/dashboards` - Lists all dashboards in the given organization. You can control the maximum number of dashboards returned through the

## Actions

- search: List dashboards (GET /api/search)
- create: Create or update a dashboard (POST /api/dashboards/db)
- get_by_id: Get dashboard by UID (GET /api/dashboards/uid/{uid})
- delete: Delete dashboard by UID (DELETE /api/dashboards/uid/{uid})
- list: List alert rules (GET /api/v1/provisioning/alert-rules)
- create_alert_rules: Create an alert rule (POST /api/v1/provisioning/alert-rules)
- list_datasources: List datasources (GET /api/datasources)
- create_dashboards: Creates a new dashboard. (POST /apis/dashboard.grafana.app/v1beta1/namespaces/:namespace/dashboards)
- create_dashboards_2: POST /apis/dashboard.grafana.app/v1beta1/namespaces/default/dashboards (POST /apis/dashboard.grafana.app/v1beta1/namespaces/default/dashboards)
- put_:uid: Updates an existing dashboard via the dashboard uid. (PUT /apis/dashboard.grafana.app/v1beta1/namespaces/:namespace/dashboards/:uid)
- create_gdxccn: POST /apis/dashboard.grafana.app/v1beta1/namespaces/default/dashboards/gdxccn (POST /apis/dashboard.grafana.app/v1beta1/namespaces/default/dashboards/gdxccn)
- list_uid: Gets a dashboard via the dashboard uid. (GET /apis/dashboard.grafana.app/v1beta1/namespaces/:namespace/dashboards/:uid)
- list_gdxccn: Example Response: (GET /apis/dashboard.grafana.app/v1beta1/namespaces/default/dashboards/gdxccn)
- list_dto: Retrieves a dashboard with additional access information. (GET /apis/dashboard.grafana.app/v1beta1/namespaces/:namespace/dashboards/:uid/dto)
- list_dashboards: Lists all dashboards in the given organization. You can control the maximum numb (GET /apis/dashboard.grafana.app/v1beta1/namespaces/:namespace/dashboards)

## Fields

- `uid`: string [REQUIRED for get_dashboard, delete_dashboard] (dashboard UID)
- `dashboard`: object [REQUIRED for create_dashboard] (dashboard JSON model)
- `overwrite`: boolean [OPTIONAL for create_dashboard] (overwrite existing dashboard)
- `title`: string [REQUIRED for create_alert] (alert rule title)
- `condition`: string [REQUIRED for create_alert] (alert condition expression)
- `query`: string [OPTIONAL for list_dashboards] (search query)
- `type`: string [OPTIONAL for list_dashboards] (filter by type: dash-db, dash-folder)

## Example Request Bodies

**Create Dashboard:**
```json
{"dashboard": {"title": "Test Dashboard", "panels": [], "timezone": "browser"}, "overwrite": false}
```

**Create Alert Rule:**
```json
{"title": "High CPU Alert", "condition": "A", "data": [{"refId": "A", "queryType": ""}]}
```
