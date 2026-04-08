---
name: opsgenie-alerts
description: Manage alerts and on-call schedules via Opsgenie. Use when the user mentions
  opsgenie, alert, on-call, schedule, escalation, incident.
version: 1.0.0
skill_type: external
base_url_env: OPSGENIE_BASE_URL
auth_env_var: OPSGENIE_API_KEY
auth_type: header
triggers:
  - opsgenie
  - alert
  - on-call
  - schedule
  - escalation
  - incident
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires OPSGENIE_BASE_URL and OPSGENIE_API_KEY environment variables.
---

# Opsgenie-Alerts

Manage alerts and on-call schedules via Opsgenie. Use when the user mentions opsgenie, alert, on-call, schedule, escalation, incident.

## API Endpoints

- **GET** `/v2/alerts` - List alerts
- **POST** `/v2/alerts` - Create alert
- **GET** `/v2/alerts/{identifier}` - Get alert
- **POST** `/v2/alerts/{identifier}/acknowledge` - Acknowledge alert
- **POST** `/v2/alerts/{identifier}/close` - Close alert
- **GET** `/v2/schedules` - List schedules
- **GET** `/v2/schedules/{identifier}/on-calls` - Get on-call
- **GET** `/v2/escalations` - List escalations

## Actions

- list: List alerts (GET /v2/alerts)
- create: Create alert (POST /v2/alerts)
- get_by_id: Get alert (GET /v2/alerts/{identifier})
- create_acknowledge: Acknowledge alert (POST /v2/alerts/{identifier}/acknowledge)
- create_close: Close alert (POST /v2/alerts/{identifier}/close)
- list_schedules: List schedules (GET /v2/schedules)
- list_on_calls: Get on-call (GET /v2/schedules/{identifier}/on-calls)
- list_escalations: List escalations (GET /v2/escalations)

## Fields

- `message`: string [REQUIRED for create]
- `priority`: string [OPTIONAL] (P1-P5)
- `description`: string [OPTIONAL]

## Example Request Bodies

**Create Alert:**
```json
{"message": "Database CPU usage above 90%", "priority": "P2", "description": "Production DB server is experiencing high CPU load"}
```

**Acknowledge Alert:**
```json
{"user": "ops-team@example.com", "note": "Investigating the issue now"}
```
