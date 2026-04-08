---
name: rapid7-security
description: Manage Rapid7 InsightVM vulnerabilities and assets. Use when the user
  mentions rapid7, insightvm, vulnerability, asset, scan, remediation.
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
- list_vulnerabilities: List asset vulnerabilities (GET /api/3/assets/{assetId}/vulnerabilities)
- list_vulnerabilities_2: List vulnerabilities (GET /api/3/vulnerabilities)
- get_by_id_vulnerabilities: Get a vulnerability (GET /api/3/vulnerabilities/{vulnId})
- list_scans: List scans (GET /api/3/scans)
- create: Start a scan (POST /api/3/sites/{siteId}/scans)
- list_sites: List sites (GET /api/3/sites)
- create_sites: Create a site (POST /api/3/sites)
- list_reports: List reports (GET /api/3/reports)

## Fields

- `name`: string [REQUIRED for create site]
- `description`: string [OPTIONAL]
- `engineId`: integer [OPTIONAL for scan]
- `hosts`: array of strings [OPTIONAL for create site]

## Example Request Bodies

**Create Site:**
```json
{"name": "Production Network", "description": "Main production environment", "hosts": ["192.168.1.0/24", "10.0.0.0/8"]}
```

**Start Scan:**
```json
{"engineId": 3}
```
