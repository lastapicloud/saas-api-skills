---
name: newrelic-monitoring
description: 'Monitor applications and query data via New Relic. Use when the user
  mentions new relic, newrelic, monitoring, apm, alert, nrql, observability.

  '
version: 1.0.0
skill_type: external
base_url_env: NEWRELIC_BASE_URL
auth_env_var: NEWRELIC_API_KEY
auth_type: header
triggers:
  - new relic
  - newrelic
  - monitoring
  - apm
  - alert
  - nrql
  - observability
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires NEWRELIC_BASE_URL and NEWRELIC_API_KEY environment variables.
annotations:
  readOnlyHint: false
  destructiveHint: false
  idempotentHint: false
---

# Newrelic-Monitoring

Monitor applications and query data via New Relic. Use when the user mentions new relic, newrelic, monitoring, apm, alert, nrql, observability.


## API Endpoints

- **GET** `/v2/applications.json` - List applications
- **GET** `/v2/applications/{id}.json` - Get application
- **POST** `/graphql` - Run NRQL query
- **GET** `/v2/alerts_policies.json` - List alert policies
- **POST** `/v2/alerts_policies.json` - Create alert policy
- **GET** `/v2/alerts_conditions.json` - List alert conditions
- **GET** `/v2/alerts_incidents.json` - List incidents

## Actions

- list: List applications (GET /v2/applications.json)
- get_application: Get application (GET /v2/applications/{id}.json)
- create: Run NRQL query (POST /graphql)
- list_alert_policies: List alert policies (GET /v2/alerts_policies.json)
- create_alert_policy: Create alert policy (POST /v2/alerts_policies.json)
- list_alert_conditions: List alert conditions (GET /v2/alerts_conditions.json)
- list_incidents: List incidents (GET /v2/alerts_incidents.json)

## Fields

- `query`: string [REQUIRED for NRQL] — Search or filter query
- `name`: string [REQUIRED for create_policy] — Display name
- `incident_preference`: string [OPTIONAL] — Incident Preference

## Example Request Bodies

**Run NRQL Query:**
```json
{"query": "{actor {account(id: 12345) {nrql(query: \"SELECT count(*) FROM Transaction SINCE 1 hour ago\") {results}}}}"}
```

**Create Alert Policy:**
```json
{"policy": {"name": "High Error Rate", "incident_preference": "PER_POLICY"}}
```

## Response

**Alerts Policies.Json object:**
- `id`: string — Unique alerts policies.json identifier
- `name`: string — Alerts Policies.Json name or title
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
