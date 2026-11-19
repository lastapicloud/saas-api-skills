---
name: qualys-vmdr
description: 'Manage vulnerability scans, view host detections, and query the knowledge
  base via the Qualys VMDR API. Use when the user mentions qualys, qualys scan, qualys
  vulnerability, VMDR, host detection, qualys knowledge base, vulnerability management.

  '
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
annotations:
  readOnlyHint: false
  destructiveHint: false
  idempotentHint: false
---

# Qualys-Vmdr

Manage vulnerability scans, view host detections, and query the knowledge base via the Qualys VMDR API. Use when the user mentions qualys, qualys scan, qualys vulnerability, VMDR, host detection, qualys knowledge base, vulnerability management.


## API Endpoints

- **POST** `/v2/events/search` - Fetch events within a date range
- **GET** `/events/ignore` - Fetch ignored events
- **POST** `/v2/incidents/search` - This API operation is used to get FIM incidents for given customer and date range after applying given filter
- **GET** `/incidents` - This API operation is used to get FIM incidents for given customer and date range after applying given filter
- **GET** `/api/2.0/fo/schedule/scan` - Download all Scheduled Report Info
- **POST** `/api/2.0/fo/knowledge_base/vuln` - Test KnowledgeBase Access
- **POST** `/msp/user_list.php` - The IP List API v2 (/api/2
- **POST** `/auth` - Generate Authenticate Generate Token
- **GET** `/ioc/events` - Get IOC Events
- **GET** `/ioc/events/count` - Get event count for a date range
- **GET** `/qps/rest/portal/version` - Get your portal version
- **POST** `/qps/rest/2.0/search/am/hostasset` - List all Agents
- **POST** `/getEndpointData` - This API operation is used to get endpoint information
- **POST** `/assets/host/count` - This API operation is used to get count of assets satisfying the filter criteria
- **POST** `/assets/host/list` - This API operation is used to get all assets data for a given customer

## Actions

- search: Fetch events within a date range (POST /v2/events/search)
- list: Fetch ignored events (GET /events/ignore)
- create_this_api_operation_is: This API operation is used to get FIM incidents for given customer and date rang (POST /v2/incidents/search)
- get_this_api_operation_is: This API operation is used to get FIM incidents for given customer and date rang (GET /incidents)
- download_scheduled_report_info: Download all Scheduled Report Info (GET /api/2.0/fo/schedule/scan)
- create: Test KnowledgeBase Access (POST /api/2.0/fo/knowledge_base/vuln)
- create_ip_list_api: The IP List API v2 (/api/2 (POST /msp/user_list.php)
- generate_authenticate_generate_token: Generate Authenticate Generate Token (POST /auth)
- get_ioc_events: Get IOC Events (GET /ioc/events)
- get_event_count_date: Get event count for a date range (GET /ioc/events/count)
- get_your_portal_version: Get your portal version (GET /qps/rest/portal/version)
- list_agents: List all Agents (POST /qps/rest/2.0/search/am/hostasset)
- create_getendpointdata: This API operation is used to get endpoint information (POST /getEndpointData)
- create_count: This API operation is used to get count of assets satisfying the filter criteria (POST /assets/host/count)
- create_list: This API operation is used to get all assets data for a given customer (POST /assets/host/list)

## Fields

- `ids`: string [OPTIONAL for list_hosts, list_host_detections, list_vulnerabilities] (comma-separated IDs to filter) — Ids
- `ips`: string [OPTIONAL for list_hosts, list_host_detections] (comma-separated IP addresses or ranges) — Ips
- `scan_ref`: string [REQUIRED for fetch_scan] (scan reference, e.g., scan/1234567890.12345) — Scan Ref
- `scan_title`: string [OPTIONAL for launch_scan] (title for the scan) — Scan title or heading
- `ip`: string [REQUIRED for launch_scan] (IP addresses or ranges to scan) — Ip
- `option_title`: string [OPTIONAL for launch_scan] (option profile title) — Option title or heading
- `details`: string [OPTIONAL for list_vulnerabilities] (detail level: Basic, All, None) — Details
- `last_modified_after`: string [OPTIONAL for list_vulnerabilities] (date filter: YYYY-MM-DD) — Last Modified After
- `status`: string [OPTIONAL for list_host_detections] (detection status: New, Active, Fixed, Re-Opened) — Current status

## Example Request Bodies

**Launch Vulnerability Scan:**
```json
{"ip": "10.0.0.1-10.0.0.255", "scan_title": "Weekly Network Scan", "option_title": "Standard Scan"}
```

**List Host Detections:**
```json
{"ips": "10.0.0.1,10.0.0.2", "status": "Active"}

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
| 400 | Invalid request body — check required fields and types |
| 401 | Authentication failed — verify API key or token is valid and not expired |
| 403 | Forbidden — insufficient permissions or scope for this action |
| 404 | Resource not found — check the ID or identifier |
| 409 | Conflict — resource already exists or concurrent modification |
| 429 | Rate limited — too many requests, retry after delay |
| 500 | Server error — retry or check service status page |
