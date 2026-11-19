---
name: statuspage-incidents
description: 'Manage Atlassian Statuspage incidents and components. Use when the user
  mentions statuspage, status page, incident, component, maintenance.

  '
version: 1.0.0
skill_type: external
base_url_env: STATUSPAGE_BASE_URL
auth_env_var: STATUSPAGE_API_KEY
auth_type: header
triggers:
  - statuspage
  - status page
  - incident
  - component
  - maintenance
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires STATUSPAGE_BASE_URL and STATUSPAGE_API_KEY environment variables.
annotations:
  readOnlyHint: false
  destructiveHint: true
  idempotentHint: false
---

# Statuspage-Incidents

Manage Atlassian Statuspage incidents and components. Use when the user mentions statuspage, status page, incident, component, maintenance.


## API Endpoints

- **GET** `/v1/pages` - List pages
- **GET** `/v1/pages/{pageId}/incidents` - List incidents
- **POST** `/v1/pages/{pageId}/incidents` - Create an incident
- **PATCH** `/v1/pages/{pageId}/incidents/{incidentId}` - Update an incident
- **DELETE** `/v1/pages/{pageId}/incidents/{incidentId}` - Delete an incident
- **GET** `/v1/pages/{pageId}/components` - List components
- **POST** `/v1/pages/{pageId}/components` - Create a component
- **PATCH** `/v1/pages/{pageId}/components/{componentId}` - Update a component
- **GET** `/v1/pages/{pageId}/incidents/scheduled` - List scheduled maintenances
- **GET** `/v1/pages/{pageId}/subscribers` - List subscribers

## Actions

- list: List pages (GET /v1/pages)
- list_incidents: List incidents (GET /v1/pages/{pageId}/incidents)
- create: Create an incident (POST /v1/pages/{pageId}/incidents)
- update: Update an incident (PATCH /v1/pages/{pageId}/incidents/{incidentId})
- delete: Delete an incident (DELETE /v1/pages/{pageId}/incidents/{incidentId})
- list_components: List components (GET /v1/pages/{pageId}/components)
- create_component: Create a component (POST /v1/pages/{pageId}/components)
- update_component: Update a component (PATCH /v1/pages/{pageId}/components/{componentId})
- list_scheduled_maintenances: List scheduled maintenances (GET /v1/pages/{pageId}/incidents/scheduled)
- list_subscribers: List subscribers (GET /v1/pages/{pageId}/subscribers)

## Fields

- `incident`: object [REQUIRED for create] with `name`, `status`, `body` — Incident configuration
- `status`: string [REQUIRED for create] ("investigating", "identified", "monitoring", "resolved") — Current status
- `component`: object [REQUIRED for create component] with `name`, `status` — Component configuration
- `component_ids`: object [OPTIONAL] (component ID to status mapping) — Component Ids configuration

## Example Request Bodies

**Create Incident:**
```json
{"incident": {"name": "API Degradation", "status": "investigating", "body": "We are investigating increased API latency."}}
```

**Create Component:**
```json
{"component": {"name": "API Gateway", "status": "operational"}}
```

## Response

**Incident object:**
- `id`: string — Unique incident identifier
- `name`: string — Incident name or title
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
