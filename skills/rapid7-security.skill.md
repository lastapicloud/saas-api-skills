---
name: rapid7-security
description: 'Manage Rapid7 InsightVM vulnerabilities and assets. Use when the user
  mentions rapid7, insightvm, vulnerability, asset, scan, remediation.

  '
version: 1.0.0
skill_type: external
base_url_env: RAPID7_BASE_URL
auth_env_var: RAPID7_API_KEY
auth_type: header
triggers:
  - rapid7
  - insightvm
  - vulnerability
  - asset
  - scan
  - remediation
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires RAPID7_BASE_URL and RAPID7_API_KEY environment variables.
annotations:
  readOnlyHint: false
  destructiveHint: false
  idempotentHint: false
---

# Rapid7-Security

Manage Rapid7 InsightVM vulnerabilities and assets. Use when the user mentions rapid7, insightvm, vulnerability, asset, scan, remediation.


## API Endpoints

- **GET** `/api/3/assets` - List assets
- **GET** `/api/3/assets/{assetId}` - Get an asset
- **GET** `/api/3/assets/{assetId}/vulnerabilities` - List asset vulnerabilities
- **GET** `/api/3/vulnerabilities` - List vulnerabilities
- **GET** `/api/3/vulnerabilities/{vulnId}` - Get a vulnerability
- **GET** `/api/3/scans` - List scans
- **POST** `/api/3/sites/{siteId}/scans` - Start a scan
- **GET** `/api/3/sites` - List sites
- **POST** `/api/3/sites` - Create a site
- **GET** `/api/3/reports` - List reports

## Actions

- list: List assets (GET /api/3/assets)
- get_by_id: Get an asset (GET /api/3/assets/{assetId})
- list_asset_vulnerabilities: List asset vulnerabilities (GET /api/3/assets/{assetId}/vulnerabilities)
- list_vulnerabilities: List vulnerabilities (GET /api/3/vulnerabilities)
- get_vulnerability: Get a vulnerability (GET /api/3/vulnerabilities/{vulnId})
- list_scans: List scans (GET /api/3/scans)
- create: Start a scan (POST /api/3/sites/{siteId}/scans)
- list_sites: List sites (GET /api/3/sites)
- create_site: Create a site (POST /api/3/sites)
- list_reports: List reports (GET /api/3/reports)

## Fields

- `name`: string [REQUIRED for create site] — Display name
- `description`: string [OPTIONAL] — Human-readable description
- `engineId`: integer [OPTIONAL for scan] — Engine unique identifier
- `hosts`: array of strings [OPTIONAL for create site] — List of hosts

## Example Request Bodies

**Create Site:**
```json
{"name": "Production Network", "description": "Main production environment", "hosts": ["192.168.1.0/24", "10.0.0.0/8"]}
```

**Start Scan:**
```json
{"engineId": 3}
```

## Response

**Asset object:**
- `id`: string — Unique asset identifier
- `name`: string — Asset name or title
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
