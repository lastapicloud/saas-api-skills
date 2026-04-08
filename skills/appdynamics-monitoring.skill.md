---
name: appdynamics-monitoring
description: Monitor applications and metrics via AppDynamics. Use when the user mentions
  appdynamics, monitoring, apm, application performance, metric, alert.
version: 1.0.0
skill_type: external
base_url_env: APPDYNAMICS_BASE_URL
auth_env_var: APPDYNAMICS_ACCESS_TOKEN
auth_type: bearer
triggers:
  - appdynamics
  - monitoring
  - apm
  - application performance
  - metric
  - alert
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires APPDYNAMICS_BASE_URL and APPDYNAMICS_ACCESS_TOKEN environment
  variables.
---

# Appdynamics-Monitoring

Monitor applications and metrics via AppDynamics. Use when the user mentions appdynamics, monitoring, apm, application performance, metric, alert.

## API Endpoints

- **GET** `/controller/rest/applications` - List applications
- **GET** `/controller/rest/applications/{applicationId}/tiers` - List tiers
- **GET** `/controller/rest/applications/{applicationId}/nodes` - List nodes
- **GET** `/controller/rest/applications/{applicationId}/metric-data` - Get metric data
- **GET** `/controller/rest/applications/{applicationId}/events` - List events
- **GET** `/controller/rest/applications/{applicationId}/problems/healthrule-violations` - List health rule violations
- **GET** `/controller/rest/applications/{applicationId}/business-transactions` - List business transactions
- **GET** `/controller/alerting/rest/v1/policies` - List alert policies
- **POST** `/controller/alerting/rest/v1/policies` - Create alert policy
- **PUT** `/controller/alerting/rest/v1/policies/{policyId}` - Update alert policy
- **DELETE** `/controller/alerting/rest/v1/policies/{policyId}` - Delete alert policy

## Actions

- list: List applications (GET /controller/rest/applications)
- list_tiers: List tiers (GET /controller/rest/applications/{applicationId}/tiers)
- list_nodes: List nodes (GET /controller/rest/applications/{applicationId}/nodes)
- list_metric_data: Get metric data (GET /controller/rest/applications/{applicationId}/metric-data)
- list_events: List events (GET /controller/rest/applications/{applicationId}/events)
- list_healthrule_violations: List health rule violations (GET /controller/rest/applications/{applicationId}/problems/healthrule-violations)
- list_business_transactions: List business transactions (GET /controller/rest/applications/{applicationId}/business-transactions)
- list_policies: List alert policies (GET /controller/alerting/rest/v1/policies)
- create_policy: Create alert policy (POST /controller/alerting/rest/v1/policies)
- update_policy: Update alert policy (PUT /controller/alerting/rest/v1/policies/{policyId})
- delete_policy: Delete alert policy (DELETE /controller/alerting/rest/v1/policies/{policyId})

## Fields

- `applicationId`: integer [REQUIRED]
- `metric-path`: string [REQUIRED for get_metrics]
- `time-range-type`: string [OPTIONAL]

## Example Request Bodies

**Get Metric Data (query parameters):**
```json
{"applicationId": 42, "metric-path": "Overall Application Performance|Average Response Time (ms)", "time-range-type": "BEFORE_NOW", "duration-in-mins": 60}
```

**List Events (query parameters):**
```json
{"applicationId": 42, "event-types": "ERROR,APPLICATION_ERROR", "severities": "ERROR,WARN"}
```
