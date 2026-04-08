---
name: sonarqube-quality
description: Analyze code quality, track issues, and retrieve metrics via the SonarQube
  API. Use when the user mentions sonarqube, sonarcloud, code quality, code smell,
  static analysis, sonar issue, technical debt, code coverage.
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
---

# Sonarqube-Quality

Analyze code quality, track issues, and retrieve metrics via the SonarQube API. Use when the user mentions sonarqube, sonarcloud, code quality, code smell, static analysis, sonar issue, technical debt, code coverage.

## API Endpoints

- **POST** `/api/projects/create` - Create a project
- **DELETE** `/api/projects/delete` - Delete a project
- **GET** `/api/projects/search` - Search for projects
- **GET** `/api/components/show` - Get component details
- **GET** `/api/measures/component` - Get measures for a component
- **GET** `/api/issues/search` - Search for issues
- **POST** `/api/issues/assign` - Assign an issue
- **POST** `/api/issues/transitions` - Transition an issue
- **GET** `/api/qualitygates/project_status` - Get quality gate status for a project
- **POST** `/api/qualitygates/set_as_default` - Set quality gate as default
- **GET** `/api/metrics/search` - Search available metrics
- **GET** `/api/hotspots/search` - Search security hotspots
- **POST** `/api/hotspots/change_status` - Change hotspot status
- **GET** `/api/hotspots/show` - Get security hotspot details

## Actions

- create: Create a project (POST /api/projects/create)
- delete: Delete a project (DELETE /api/projects/delete)
- search: Search for projects (GET /api/projects/search)
- show: Get component details (GET /api/components/show)
- list_measures: Get measures for a component (GET /api/measures/component)
- search_issues: Search for issues (GET /api/issues/search)
- assign_issue: Assign an issue (POST /api/issues/assign)
- transition_issue: Transition an issue (POST /api/issues/transitions)
- project_status: Get quality gate status (GET /api/qualitygates/project_status)
- set_default_qg: Set quality gate as default (POST /api/qualitygates/set_as_default)
- search_metrics: Search available metrics (GET /api/metrics/search)
- search_hotspots: Search security hotspots (GET /api/hotspots/search)
- change_hotspot: Change hotspot status (POST /api/hotspots/change_status)
- show_hotspot: Get hotspot details (GET /api/hotspots/show)

## Fields

- `component`: string [REQUIRED for get_component, get_measures] (component key, usually project key)
- `metricKeys`: string [REQUIRED for get_measures] (comma-separated metric keys: ncloc, code_smells, bugs, vulnerabilities, coverage)
- `projectKey`: string [OPTIONAL for search_issues, get_quality_gate_status] (project key filter)
- `componentKeys`: string [OPTIONAL for search_issues] (comma-separated component keys)
- `severities`: string [OPTIONAL for search_issues] (comma-separated: INFO, MINOR, MAJOR, CRITICAL, BLOCKER)
- `statuses`: string [OPTIONAL for search_issues] (comma-separated: OPEN, CONFIRMED, REOPENED, RESOLVED, CLOSED)
- `types`: string [OPTIONAL for search_issues] (comma-separated: CODE_SMELL, BUG, VULNERABILITY, SECURITY_HOTSPOT)
- `hotspot`: string [REQUIRED for get_hotspot] (hotspot key)

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
