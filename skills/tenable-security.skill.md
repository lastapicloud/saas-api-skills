---
name: tenable-security
description: 'Manage Tenable.io vulnerabilities, assets, and scans. Use when the user
  mentions tenable, vulnerability, asset, scan, nessus.

  '
version: 1.0.0
skill_type: external
base_url_env: TENABLE_BASE_URL
auth_env_var: TENABLE_SECRET_KEY
auth_type: header
triggers:
  - tenable
  - vulnerability
  - asset
  - scan
  - nessus
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires TENABLE_BASE_URL and TENABLE_SECRET_KEY environment variables.
annotations:
  readOnlyHint: false
  destructiveHint: false
  idempotentHint: false
---

# Tenable-Security

Manage Tenable.io vulnerabilities, assets, and scans. Use when the user mentions tenable, vulnerability, asset, scan, nessus.


## API Endpoints

- **GET** `/assets` - List assets
- **GET** `/assets/{assetId}` - Get an asset
- **GET** `/scans` - List scans
- **POST** `/scans` - Create a scan
- **POST** `/scans/{scanId}/launch` - Launch a scan
- **GET** `/scans/{scanId}` - Get scan details
- **GET** `/vulns` - List vulnerabilities
- **GET** `/vulns/{vulnId}` - Get vulnerability details
- **GET** `/workbenches/assets` - Export assets
- **GET** `/workbenches/vulnerabilities` - Export vulnerabilities

## Actions

- list: List assets (GET /assets)
- get_by_id: Get an asset (GET /assets/{assetId})
- list_scans: List scans (GET /scans)
- create: Create a scan (POST /scans)
- create_launch_scan: Launch a scan (POST /scans/{scanId}/launch)
- get_scan_details: Get scan details (GET /scans/{scanId})
- list_vulnerabilities: List vulnerabilities (GET /vulns)
- get_vulnerability_details: Get vulnerability details (GET /vulns/{vulnId})
- export_assets: Export assets (GET /workbenches/assets)
- export_vulnerabilities: Export vulnerabilities (GET /workbenches/vulnerabilities)

## Fields

- `uuid`: string [REQUIRED for create scan] (template UUID) — Uu unique identifier
- `settings`: object [REQUIRED for create scan] with `name`, `text_targets` — Settings configuration
- `name`: string [REQUIRED in settings] — Display name
- `text_targets`: string [REQUIRED in settings] (comma-separated IPs) — Text Targets

## Example Request Bodies

**Create Scan:**
```json
{"uuid": "template-uuid-abc123", "settings": {"name": "Weekly Network Scan", "text_targets": "192.168.1.0/24,10.0.0.0/8"}}
```

**Launch Scan:**
```json
{}
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
