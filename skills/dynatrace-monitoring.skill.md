---
name: dynatrace-monitoring
description: Monitor applications and infrastructure via Dynatrace. Use when the user
  mentions dynatrace, monitoring, apm, observability, metric, problem, host.
version: 1.0.0
skill_type: external
base_url_env: DYNATRACE_BASE_URL
auth_env_var: DYNATRACE_API_TOKEN
auth_type: header
triggers:
  - dynatrace
  - monitoring
  - apm
  - observability
  - metric
  - problem
  - host
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires DYNATRACE_BASE_URL and DYNATRACE_API_TOKEN environment variables.
---

# Dynatrace-Monitoring

Monitor applications and infrastructure via Dynatrace. Use when the user mentions dynatrace, monitoring, apm, observability, metric, problem, host.

## API Endpoints

- **GET** `/api/v2/entities` - List entities
- **GET** `/api/v2/entities/{entityId}` - Get entity by ID
- **GET** `/api/v2/problems` - List problems
- **GET** `/api/v2/problems/{problemId}` - Get problem by ID
- **POST** `/api/v2/problems/{problemId}/close` - Close a problem
- **GET** `/api/v2/metrics` - List metrics
- **POST** `/api/v2/metrics/query` - Query metrics
- **GET** `/api/v2/settings/schemas` - List setting schemas

## Actions

- list: List entities (GET /api/v2/entities)
- get_by_id: Get entity by ID (GET /api/v2/entities/{entityId})
- list_problems: List problems (GET /api/v2/problems)
- get_by_id_problems: Get problem by ID (GET /api/v2/problems/{problemId})
- create: Close a problem (POST /api/v2/problems/{problemId}/close)
- list_metrics: List metrics (GET /api/v2/metrics)
- query: Query metrics (POST /api/v2/metrics/query)
- list_schemas: List setting schemas (GET /api/v2/settings/schemas)

## Fields

- `entitySelector`: string [OPTIONAL] (entity filter)
- `from`: string [OPTIONAL] (time range start)
- `to`: string [OPTIONAL] (time range end)
- `metricSelector`: string [REQUIRED for query_metrics]

## Example Request Bodies

**Query Metrics:**
```json
{"metricSelector": "builtin:host.cpu.usage", "from": "now-2h", "to": "now"}
```

**Close Problem:**
```json
{"message": "Issue resolved after scaling up resources"}
