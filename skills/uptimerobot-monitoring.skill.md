---
name: uptimerobot-monitoring
description: 'Manage UptimeRobot monitors and alert contacts. Use when the user mentions
  uptimerobot, uptime, monitor, alert, status.

  '
version: 1.0.0
skill_type: external
base_url_env: UPTIMEROBOT_BASE_URL
auth_env_var: UPTIMEROBOT_API_KEY
auth_type: header
triggers:
  - uptimerobot
  - uptime
  - monitor
  - alert
  - status
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires UPTIMEROBOT_BASE_URL and UPTIMEROBOT_API_KEY environment variables.
annotations:
  readOnlyHint: false
  destructiveHint: false
  idempotentHint: false
---

# Uptimerobot-Monitoring

Manage UptimeRobot monitors and alert contacts. Use when the user mentions uptimerobot, uptime, monitor, alert, status.


## API Endpoints

- **POST** `/v2/getMonitors` - List monitors
- **POST** `/v2/newMonitor` - Create a monitor
- **POST** `/v2/editMonitor` - Update a monitor
- **POST** `/v2/deleteMonitor` - Delete a monitor
- **POST** `/v2/resetMonitor` - Reset a monitor
- **POST** `/v2/getAlertContacts` - List alert contacts
- **POST** `/v2/newAlertContact` - Create an alert contact
- **POST** `/v2/getAccountDetails` - Get account details
- **POST** `/v2/getMWindows` - List maintenance windows
- **POST** `/v2/getPSPs` - List public status pages

## Actions

- create: List monitors (POST /v2/getMonitors)
- create_monitor: Create a monitor (POST /v2/newMonitor)
- update_monitor: Update a monitor (POST /v2/editMonitor)
- delete_monitor: Delete a monitor (POST /v2/deleteMonitor)
- create_reset_monitor: Reset a monitor (POST /v2/resetMonitor)
- list_alert_contacts: List alert contacts (POST /v2/getAlertContacts)
- create_alert_contact: Create an alert contact (POST /v2/newAlertContact)
- get_account_details: Get account details (POST /v2/getAccountDetails)
- list_maintenance_windows: List maintenance windows (POST /v2/getMWindows)
- list_public_status_pages: List public status pages (POST /v2/getPSPs)

## Fields

- `friendly_name`: string [REQUIRED for create] — Friendly display name
- `url`: string [REQUIRED for create] — URL
- `type`: integer [REQUIRED for create] (1=HTTP, 2=keyword, 3=ping, 4=port) — Resource type
- `interval`: integer [OPTIONAL] (seconds, minimum 60) — Interval value
- `alert_contacts`: string [OPTIONAL] (contact IDs) — Alert Contacts

## Example Request Bodies

**Create Monitor:**
```json
{"friendly_name": "Production API", "url": "https://api.example.com/health", "type": 1, "interval": 300}
```

**Update Monitor:**
```json
{"friendly_name": "Production API v2", "url": "https://api-v2.example.com/health", "interval": 60}

## Response

**Getmonitor object:**
- `id`: string — Unique getmonitor identifier
- `name`: string — Getmonitor name or title
- `status`: string — Current status
- `created_at`: string — Creation timestamp (ISO 8601)
- `updated_at`: string — Last update timestamp (ISO 8601)

## Error Responses

| Status | Meaning |
|--------|---------|
| 400 | Invalid request body — check required fields and types |
| 401 | Authentication failed — verify API key or token is valid and not expired |
| 403 | Forbidden — insufficient permissions or scope for this action |
| 409 | Conflict — resource already exists or concurrent modification |
| 429 | Rate limited — too many requests, retry after delay |
| 500 | Server error — retry or check service status page |
