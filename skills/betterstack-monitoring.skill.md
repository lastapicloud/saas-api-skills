---
name: betterstack-monitoring
description: Manage uptime monitors and incidents via Better Stack. Use when the user
  mentions better stack, betterstack, uptime, monitor, incident, status page.
version: 1.0.0
skill_type: external
base_url_env: BETTERSTACK_BASE_URL
auth_env_var: BETTERSTACK_API_TOKEN
auth_type: bearer
triggers:
  - better stack
  - betterstack
  - uptime
  - monitor
  - incident
  - status page
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires BETTERSTACK_BASE_URL and BETTERSTACK_API_TOKEN environment
  variables.
---

# Betterstack-Monitoring

Manage uptime monitors and incidents via Better Stack. Use when the user mentions better stack, betterstack, uptime, monitor, incident, status page.

## API Endpoints

- **GET** `/api/v2/monitors` - List monitors
- **POST** `/api/v2/monitors` - Create a monitor
- **GET** `/api/v2/monitors/{monitor_id}` - Get monitor by ID
- **PATCH** `/api/v2/monitors/{monitor_id}` - Update a monitor
- **DELETE** `/api/v2/monitors/{monitor_id}` - Delete a monitor
- **GET** `/api/v2/incidents` - List incidents
- **GET** `/api/v2/heartbeats` - List heartbeats
- **POST** `/api/v2/heartbeats` - Create a heartbeat

## Actions

- list: List monitors (GET /api/v2/monitors)
- create: Create a monitor (POST /api/v2/monitors)
- get_by_id: Get monitor by ID (GET /api/v2/monitors/{monitor_id})
- update: Update a monitor (PATCH /api/v2/monitors/{monitor_id})
- delete: Delete a monitor (DELETE /api/v2/monitors/{monitor_id})
- list_incidents: List incidents (GET /api/v2/incidents)
- list_heartbeats: List heartbeats (GET /api/v2/heartbeats)
- create_heartbeats: Create a heartbeat (POST /api/v2/heartbeats)

## Fields

- `url`: string [REQUIRED for create]
- `monitor_type`: string [REQUIRED for create] (status, ping, etc.)
- `check_frequency`: integer [OPTIONAL] (seconds)

## Example Request Bodies

**Create Monitor:**
```json
{"url": "https://example.com", "monitor_type": "status", "check_frequency": 300}
```

**Update Monitor:**
```json
{"url": "https://example.com/health", "check_frequency": 60}
