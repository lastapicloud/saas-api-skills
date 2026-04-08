---
name: newrelic-monitoring
description: Monitor applications and query data via New Relic. Use when the user
  mentions new relic, newrelic, monitoring, apm, alert, nrql, observability.
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
- list_applications: Get application (GET /v2/applications/{id}.json)
- create: Run NRQL query (POST /graphql)
- list_alerts_policies_json: List alert policies (GET /v2/alerts_policies.json)
- create_alerts_policies_json: Create alert policy (POST /v2/alerts_policies.json)
- list_alerts_conditions_json: List alert conditions (GET /v2/alerts_conditions.json)
- list_alerts_incidents_json: List incidents (GET /v2/alerts_incidents.json)

## Fields

- `query`: string [REQUIRED for NRQL]
- `name`: string [REQUIRED for create_policy]
- `incident_preference`: string [OPTIONAL]

## Example Request Bodies

**Run NRQL Query:**
```json
{"query": "{actor {account(id: 12345) {nrql(query: \"SELECT count(*) FROM Transaction SINCE 1 hour ago\") {results}}}}"}
```

**Create Alert Policy:**
```json
{"policy": {"name": "High Error Rate", "incident_preference": "PER_POLICY"}}
```
