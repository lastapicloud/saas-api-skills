---
name: tenable-security
description: Manage Tenable.io vulnerabilities, assets, and scans. Use when the user
  mentions tenable, vulnerability, asset, scan, nessus.
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
- create_launch: Launch a scan (POST /scans/{scanId}/launch)
- get_by_id_scans: Get scan details (GET /scans/{scanId})
- list_vulns: List vulnerabilities (GET /vulns)
- get_by_id_vulns: Get vulnerability details (GET /vulns/{vulnId})
- list_assets: Export assets (GET /workbenches/assets)
- list_vulnerabilities: Export vulnerabilities (GET /workbenches/vulnerabilities)

## Fields

- `uuid`: string [REQUIRED for create scan] (template UUID)
- `settings`: object [REQUIRED for create scan] with `name`, `text_targets`
- `name`: string [REQUIRED in settings]
- `text_targets`: string [REQUIRED in settings] (comma-separated IPs)

## Example Request Bodies

**Create Scan:**
```json
{"uuid": "template-uuid-abc123", "settings": {"name": "Weekly Network Scan", "text_targets": "192.168.1.0/24,10.0.0.0/8"}}
```

**Launch Scan:**
```json
{}
```
