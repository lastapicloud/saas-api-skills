---
name: uptimerobot-monitoring
description: Manage UptimeRobot monitors and alert contacts. Use when the user mentions
  uptimerobot, uptime, monitor, alert, status.
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
- create_newmonitor: Create a monitor (POST /v2/newMonitor)
- create_editmonitor: Update a monitor (POST /v2/editMonitor)
- create_deletemonitor: Delete a monitor (POST /v2/deleteMonitor)
- create_resetmonitor: Reset a monitor (POST /v2/resetMonitor)
- create_getalertcontacts: List alert contacts (POST /v2/getAlertContacts)
- create_newalertcontact: Create an alert contact (POST /v2/newAlertContact)
- create_getaccountdetails: Get account details (POST /v2/getAccountDetails)
- create_getmwindows: List maintenance windows (POST /v2/getMWindows)
- create_getpsps: List public status pages (POST /v2/getPSPs)

## Fields

- `friendly_name`: string [REQUIRED for create]
- `url`: string [REQUIRED for create]
- `type`: integer [REQUIRED for create] (1=HTTP, 2=keyword, 3=ping, 4=port)
- `interval`: integer [OPTIONAL] (seconds, minimum 60)
- `alert_contacts`: string [OPTIONAL] (contact IDs)

## Example Request Bodies

**Create Monitor:**
```json
{"friendly_name": "Production API", "url": "https://api.example.com/health", "type": 1, "interval": 300}
```

**Update Monitor:**
```json
{"friendly_name": "Production API v2", "url": "https://api-v2.example.com/health", "interval": 60}
