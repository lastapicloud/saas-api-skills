---
name: semgrep-sast
description: 'Manage Semgrep code scanning deployments and findings. Use when the
  user mentions semgrep, SAST, code scan, finding, vulnerability, static analysis.

  '
version: 1.0.0
skill_type: external
base_url_env: SEMGREP_BASE_URL
auth_env_var: SEMGREP_API_TOKEN
auth_type: bearer
triggers:
  - semgrep
  - SAST
  - code scan
  - finding
  - vulnerability
  - static analysis
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires SEMGREP_BASE_URL and SEMGREP_API_TOKEN environment variables.
annotations:
  readOnlyHint: false
  destructiveHint: false
  idempotentHint: true
---

# Semgrep-Sast

Manage Semgrep code scanning deployments and findings. Use when the user mentions semgrep, SAST, code scan, finding, vulnerability, static analysis.


## API Endpoints

- **GET** `/api/v1/deployments` - List deployments
- **GET** `/api/v1/deployments/{deploymentId}/findings` - List findings
- **GET** `/api/v1/deployments/{deploymentId}/findings/{findingId}` - Get a finding
- **PUT** `/api/v1/deployments/{deploymentId}/findings/{findingId}/triage` - Triage a finding
- **GET** `/api/v1/deployments/{deploymentId}/projects` - List projects
- **GET** `/api/v1/deployments/{deploymentId}/scans` - List scans
- **GET** `/api/v1/deployments/{deploymentId}/rules` - List rules
- **GET** `/api/v1/deployments/{deploymentId}/stats` - Get statistics

## Actions

- list: List deployments (GET /api/v1/deployments)
- list_findings: List findings (GET /api/v1/deployments/{deploymentId}/findings)
- get_by_id: Get a finding (GET /api/v1/deployments/{deploymentId}/findings/{findingId})
- put_triage: Triage a finding (PUT /api/v1/deployments/{deploymentId}/findings/{findingId}/triage)
- list_projects: List projects (GET /api/v1/deployments/{deploymentId}/projects)
- list_scans: List scans (GET /api/v1/deployments/{deploymentId}/scans)
- list_rules: List rules (GET /api/v1/deployments/{deploymentId}/rules)
- get_statistics: Get statistics (GET /api/v1/deployments/{deploymentId}/stats)

## Fields

- `state`: string [REQUIRED for triage] (e.g., "open", "ignored", "fixed") — State or region
- `reason`: string [OPTIONAL for triage] — Reason
- `severity`: string [OPTIONAL for filter] (e.g., "error", "warning", "info") — Severity

## Example Request Bodies

**Triage Finding:**
```json
{"state": "ignored", "reason": "False positive - test file only"}
```

**List Findings with Filter:**
```json
{"severity": "error"}

## Response

**Finding object:**
- `id`: string — Unique finding identifier
- `name`: string — Finding name or title
- `status`: string — Current status
- `created_at`: string — Creation timestamp (ISO 8601)
- `updated_at`: string — Last update timestamp (ISO 8601)

## Error Responses

| Status | Meaning |
|--------|---------|
| 400 | Invalid request body — check required fields and types |
| 401 | Authentication failed — verify API key or token is valid and not expired |
| 404 | Resource not found — check the ID or identifier |
| 429 | Rate limited — too many requests, retry after delay |
| 500 | Server error — retry or check service status page |
