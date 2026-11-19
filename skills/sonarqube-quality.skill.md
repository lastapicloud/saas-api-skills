---
name: sonarqube-quality
description: 'Analyze code quality, track issues, and retrieve metrics via the SonarQube
  API. Use when the user mentions sonarqube, sonarcloud, code quality, code smell,
  static analysis, sonar issue, technical debt, code coverage.

  '
version: 1.0.0
skill_type: external
base_url_env: SONARQUBE_BASE_URL
auth_env_var: SONARQUBE_API_TOKEN
auth_type: bearer
triggers:
  - sonarqube
  - sonarcloud
  - code quality
  - code smell
  - static analysis
  - sonar issue
  - technical debt
  - code coverage
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires SONARQUBE_BASE_URL and SONARQUBE_API_TOKEN environment variables.
annotations:
  readOnlyHint: true
  destructiveHint: false
  idempotentHint: false
---

# Sonarqube-Quality

Analyze code quality, track issues, and retrieve metrics via the SonarQube API. Use when the user mentions sonarqube, sonarcloud, code quality, code smell, static analysis, sonar issue, technical debt, code coverage.


## API Endpoints

- **GET** `/api/projects/search` - Search for projects
- **GET** `/api/components/show` - Get component details
- **GET** `/api/measures/component` - Get measures for a component
- **GET** `/api/issues/search` - Search for issues
- **GET** `/api/qualitygates/project_status` - Get quality gate status for a project
- **GET** `/api/metrics/search` - Search available metrics
- **GET** `/api/hotspots/search` - Search security hotspots
- **GET** `/api/hotspots/show` - Get security hotspot details

## Actions

- search: Search for projects (GET /api/projects/search)
- list: Get component details (GET /api/components/show)
- get_measures_component: Get measures for a component (GET /api/measures/component)
- search_issues: Search for issues (GET /api/issues/search)
- get_quality_gate_status: Get quality gate status for a project (GET /api/qualitygates/project_status)
- search_available_metrics: Search available metrics (GET /api/metrics/search)
- search_security_hotspots: Search security hotspots (GET /api/hotspots/search)
- get_security_hotspot_details: Get security hotspot details (GET /api/hotspots/show)

## Fields

- `component`: string [REQUIRED for get_component, get_measures] (component key, usually project key) — Component
- `metricKeys`: string [REQUIRED for get_measures] (comma-separated metric keys: ncloc, code_smells, bugs, vulnerabilities, coverage) — Metrickeys
- `projectKey`: string [OPTIONAL for search_issues, get_quality_gate_status] (project key filter) — Project api key or identifier
- `componentKeys`: string [OPTIONAL for search_issues] (comma-separated component keys) — Componentkeys
- `severities`: string [OPTIONAL for search_issues] (comma-separated: INFO, MINOR, MAJOR, CRITICAL, BLOCKER) — Severities
- `statuses`: string [OPTIONAL for search_issues] (comma-separated: OPEN, CONFIRMED, REOPENED, RESOLVED, CLOSED) — Statuses
- `types`: string [OPTIONAL for search_issues] (comma-separated: CODE_SMELL, BUG, VULNERABILITY, SECURITY_HOTSPOT) — Types
- `hotspot`: string [REQUIRED for get_hotspot] (hotspot key) — Hotspot

## Example Request Bodies

**Search Issues (query params):**
```json
{
  "componentKeys": "my-project",
  "severities": "CRITICAL,BLOCKER",
  "types": "BUG,VULNERABILITY",
  "statuses": "OPEN,CONFIRMED"
}
```

**Get Measures (query params):**
```json
{
  "component": "my-project",
  "metricKeys": "ncloc,bugs,vulnerabilities,code_smells,coverage"
}
```

## Response

**Search object:**
- `id`: string — Unique search identifier
- `name`: string — Search name or title
- `status`: string — Current status
- `created_at`: string — Creation timestamp (ISO 8601)
- `updated_at`: string — Last update timestamp (ISO 8601)

## Error Responses

| Status | Meaning |
|--------|---------|
| 401 | Authentication failed — verify API key or token is valid and not expired |
| 404 | Resource not found — check the ID or identifier |
| 429 | Rate limited — too many requests, retry after delay |
| 500 | Server error — retry or check service status page |
