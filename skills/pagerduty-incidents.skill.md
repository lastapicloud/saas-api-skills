---
name: pagerduty-incidents
description: Manage incidents, services, and on-call schedules in PagerDuty. Use when
  the user mentions pagerduty, incident, alert, on-call, escalate.
version: 1.0.0
skill_type: external
base_url_env: PAGERDUTY_BASE_URL
auth_env_var: PAGERDUTY_API_TOKEN
auth_type: bearer
triggers:
  - pagerduty
  - incident
  - alert
  - on-call
  - escalate
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires PAGERDUTY_BASE_URL and PAGERDUTY_API_TOKEN environment variables.
---

# Pagerduty-Incidents

Manage incidents, services, and on-call schedules in PagerDuty. Use when the user mentions pagerduty, incident, alert, on-call, escalate.

## API Endpoints

- **GET** `/incidents` - List incidents
- **POST** `/incidents` - Create an incident
- **PUT** `/incidents/{id}` - Acknowledge an incident
- **PUT** `/incidents/{id}` - Resolve an incident
- **GET** `/services` - List services
- **GET** `/oncalls` - List on-call users
- **GET** `/addons` - List installed Add-ons
- **POST** `/addons` - Install an Add-on
- **PUT** `/addons/{id}` - Update an Add-on
- **DELETE** `/addons/{id}` - Delete an Add-on
- **GET** `/alert_grouping_settings` - List alert grouping settings
- **POST** `/alert_grouping_settings` - Create an Alert Grouping Setting
- **PUT** `/alert_grouping_settings/{id}` - Update an Alert Grouping Setting
- **DELETE** `/alert_grouping_settings/{id}` - Delete an Alert Grouping Setting
- **GET** `/escalation_policies` - List escalation policies

## Actions

- list: List incidents (GET /incidents)
- create: Create an incident (POST /incidents)
- update: Acknowledge an incident (PUT /incidents/{id})
- update_incidents: Resolve an incident (PUT /incidents/{id})
- list_services: List services (GET /services)
- list_oncalls: List on-call users (GET /oncalls)
- list_addons: List installed Add-ons (GET /addons)
- create_addons: Install an Add-on (POST /addons)
- update_addons: Update an Add-on (PUT /addons/{id})
- delete: Delete an Add-on (DELETE /addons/{id})
- list_alert_grouping_settings: List alert grouping settings (GET /alert_grouping_settings)
- create_alert_grouping_settings: Create an Alert Grouping Setting (POST /alert_grouping_settings)
- update_alert_grouping_settings: Update an Alert Grouping Setting (PUT /alert_grouping_settings/{id})
- delete_alert_grouping_settings: Delete an Alert Grouping Setting (DELETE /alert_grouping_settings/{id})
- list_escalation_policies: List escalation policies (GET /escalation_policies)

## Fields

- `id`: string [REQUIRED for acknowledge_incident, resolve_incident] (incident ID)
- `title`: string [REQUIRED for create_incident] (incident title)
- `service`: object [REQUIRED for create_incident] (service reference, e.g. {"id": "...", "type": "service_reference"})
- `urgency`: string [OPTIONAL] (high or low)
- `body`: object [OPTIONAL for create_incident] (incident body details)
- `status`: string [OPTIONAL for list_incidents] (triggered, acknowledged, resolved)
- `escalation_policy_ids[]`: array [OPTIONAL for list_oncalls] (filter by escalation policy)

## Example Request Bodies

**Create Incident:**
```json
{"incident": {"type": "incident", "title": "Server Down", "service": {"id": "PSERVICE1", "type": "service_reference"}, "urgency": "high", "body": {"type": "incident_body", "details": "Production server is not responding"}}}
```

**Acknowledge Incident:**
```json
{"incident": {"type": "incident_reference", "status": "acknowledged"}}
```

**Resolve Incident:**
```json
{"incident": {"type": "incident_reference", "status": "resolved"}}
```
