---
name: monte-carlo-observability
description: Data observability via Monte Carlo. Use when the user mentions monte carlo, data observability, data quality, data lineage, anomaly detection.
version: 1.0.0
skill_type: external
base_url_env: MONTE_CARLO_BASE_URL
auth_env_var: MONTE_CARLO_API_KEY
auth_type: bearer
triggers:
  - monte carlo
  - data observability
  - data quality
  - data lineage
  - anomaly detection
license: Proprietary
metadata:
  author: lastapi
  version: 1.0.0
  documentation: https://docs.getmontecarlo.com/
---

# Monte-Carlo-Observability

Data observability via Monte Carlo. Use when the user mentions monte carlo, data observability, data quality, data lineage, anomaly detection.

## API Endpoints

- **GET** `/monitors` - List monitors
- **POST** `/monitors` - Create monitor
- **GET** `/monitors/{id}` - Get monitor
- **PATCH** `/monitors/{id}` - Update monitor
- **DELETE** `/monitors/{id}` - Delete monitor
- **GET** `/incidents` - List incidents
- **GET** `/incidents/{id}` - Get incident
- **POST** `/incidents/{id}/acknowledge` - Acknowledge incident
- **POST** `/incidents/{id}/resolve` - Resolve incident
- **GET** `/lineage` - Get data lineage
- **GET** `/tables` - List tables
- **GET** `/tables/{id}/statistics` - Get table statistics

## Actions

- list_monitors: List monitors (GET /monitors)
- create_monitor: Create monitor (POST /monitors)
- get_monitor: Get monitor (GET /monitors/{id})
- update_monitor: Update monitor (PATCH /monitors/{id})
- delete_monitor: Delete monitor (DELETE /monitors/{id})
- list_incidents: List incidents (GET /incidents)
- get_incident: Get incident (GET /incidents/{id})
- acknowledge_incident: Acknowledge incident (POST /incidents/{id}/acknowledge)
- resolve_incident: Resolve incident (POST /incidents/{id}/resolve)
- get_lineage: Get data lineage (GET /lineage)
- list_tables: List tables (GET /tables)
- get_table_stats: Get table statistics (GET /tables/{id}/statistics)

## Fields

- `name`: string [REQUIRED for create] - Monitor name
- `type`: string [REQUIRED for create] - Monitor type (volume, freshness, schema)
- `table`: string [REQUIRED] - Table name
- `query`: string [OPTIONAL] - SQL query for custom monitors
- `threshold`: number [OPTIONAL] - Alert threshold

## Example Request Bodies

**Create Monitor:**
```json
{"name": "Table Freshness", "type": "freshness", "table": "users", "threshold": 3600}
```

**Create Volume Monitor:**
```json
{"name": "Daily Volume Check", "type": "volume", "query": "SELECT count(*) FROM events", "threshold": 1000}
```
