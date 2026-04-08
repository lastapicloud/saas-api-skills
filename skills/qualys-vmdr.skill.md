---
name: qualys-vmdr
description: Manage vulnerability scans, view host detections, and query the knowledge
  base via the Qualys VMDR API. Use when the user mentions qualys, qualys scan, qualys
  vulnerability, VMDR, host detection, qualys knowledge base, vulnerability management.
version: 1.0.0
skill_type: external
base_url_env: QUALYS_BASE_URL
auth_env_var: QUALYS_API_TOKEN
auth_user_env: QUALYS_USERNAME
auth_type: basic
triggers:
  - qualys
  - qualys scan
  - qualys vulnerability
  - VMDR
  - host detection
  - qualys knowledge base
  - vulnerability management
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires QUALYS_BASE_URL and QUALYS_API_TOKEN environment variables.
---

# Qualys-Vmdr

Manage vulnerability scans, view host detections, and query the knowledge base via the Qualys VMDR API. Use when the user mentions qualys, qualys scan, qualys vulnerability, VMDR, host detection, qualys knowledge base, vulnerability management.

## API Endpoints

- **POST** `/api/2.0/fo/asset/host/?action=list` - List scanned hosts
- **POST** `/api/2.0/fo/asset/host/vm/detection/?action=list` - List host vulnerability detections
- **POST** `/api/2.0/fo/knowledge_base/vuln/?action=list` - List vulnerabilities in the knowledge base
- **POST** `/api/2.0/fo/scan/?action=list` - List vulnerability scans
- **POST** `/api/2.0/fo/scan/?action=launch` - Launch a vulnerability scan
- **POST** `/api/2.0/fo/scan/?action=fetch` - Fetch scan results
- **POST** `/api/2.0/fo/report/?action=list` - List reports
- **GET** `/api/2.0/fo/appliance/?action=list` - List scanner appliances

## Actions

- create: List scanned hosts (POST /api/2.0/fo/asset/host/?action=list)
- create_actionlist: List host vulnerability detections (POST /api/2.0/fo/asset/host/vm/detection/?action=list)
- create_actionlist_2: List vulnerabilities in the knowledge base (POST /api/2.0/fo/knowledge_base/vuln/?action=list)
- create_actionlist_3: List vulnerability scans (POST /api/2.0/fo/scan/?action=list)
- create_actionlaunch: Launch a vulnerability scan (POST /api/2.0/fo/scan/?action=launch)
- create_actionfetch: Fetch scan results (POST /api/2.0/fo/scan/?action=fetch)
- create_actionlist_4: List reports (POST /api/2.0/fo/report/?action=list)
- list: List scanner appliances (GET /api/2.0/fo/appliance/?action=list)

## Fields

- `ids`: string [OPTIONAL for list_hosts, list_host_detections, list_vulnerabilities] (comma-separated IDs to filter)
- `ips`: string [OPTIONAL for list_hosts, list_host_detections] (comma-separated IP addresses or ranges)
- `scan_ref`: string [REQUIRED for fetch_scan] (scan reference, e.g., scan/1234567890.12345)
- `scan_title`: string [OPTIONAL for launch_scan] (title for the scan)
- `ip`: string [REQUIRED for launch_scan] (IP addresses or ranges to scan)
- `option_title`: string [OPTIONAL for launch_scan] (option profile title)
- `details`: string [OPTIONAL for list_vulnerabilities] (detail level: Basic, All, None)
- `last_modified_after`: string [OPTIONAL for list_vulnerabilities] (date filter: YYYY-MM-DD)
- `status`: string [OPTIONAL for list_host_detections] (detection status: New, Active, Fixed, Re-Opened)

## Example Request Bodies

**Launch Vulnerability Scan:**
```json
{"ip": "10.0.0.1-10.0.0.255", "scan_title": "Weekly Network Scan", "option_title": "Standard Scan"}
```

**List Host Detections:**
```json
{"ips": "10.0.0.1,10.0.0.2", "status": "Active"}
