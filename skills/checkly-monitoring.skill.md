---
name: checkly-monitoring
description: Manage Checkly API checks, browser checks, and alerts. Use when the user
  mentions checkly, check, monitoring, API check, browser check, synthetic.
version: 1.0.0
skill_type: external
base_url_env: CHECKLY_BASE_URL
auth_env_var: CHECKLY_API_KEY
auth_type: bearer
triggers:
  - checkly
  - check
  - monitoring
  - API check
  - browser check
  - synthetic
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires CHECKLY_BASE_URL and CHECKLY_API_KEY environment variables.
---

# Checkly-Monitoring

Manage Checkly API checks, browser checks, and alerts. Use when the user mentions checkly, check, monitoring, API check, browser check, synthetic.

## API Endpoints

- **GET** `/v1/checks` - List checks
- **GET** `/v1/checks/{checkId}` - Get a check
- **POST** `/v1/checks/api` - Create an API check
- **POST** `/v1/checks/browser` - Create a browser check
- **PUT** `/v1/checks/{checkId}` - Update a check
- **DELETE** `/v1/checks/{checkId}` - Delete a check
- **GET** `/v1/check-results/{checkId}` - List check results
- **GET** `/v1/check-groups` - List check groups
- **POST** `/v1/check-groups` - Create a check group
- **GET** `/v1/alert-channels` - List alert channels

## Actions

- list: List checks (GET /v1/checks)
- get_by_id: Get a check (GET /v1/checks/{checkId})
- create: Create an API check (POST /v1/checks/api)
- create_browser: Create a browser check (POST /v1/checks/browser)
- update: Update a check (PUT /v1/checks/{checkId})
- delete: Delete a check (DELETE /v1/checks/{checkId})
- get_by_id_check_results: List check results (GET /v1/check-results/{checkId})
- list_check_groups: List check groups (GET /v1/check-groups)
- create_check_groups: Create a check group (POST /v1/check-groups)
- list_alert_channels: List alert channels (GET /v1/alert-channels)

## Fields

- `name`: string [REQUIRED for create]
- `activated`: boolean [REQUIRED]
- `frequency`: integer [REQUIRED] (seconds, e.g., 60, 300, 600)
- `locations`: array [REQUIRED] (e.g., ["us-east-1", "eu-west-1"])
- `request`: object [REQUIRED for API check] with `url`, `method`
- `script`: string [REQUIRED for browser check] (Playwright script)

## Example Request Bodies

**Create API Check:**
```json
{"name": "Homepage Check", "activated": true, "frequency": 300, "locations": ["us-east-1", "eu-west-1"], "request": {"url": "https://example.com", "method": "GET"}}
```

**Update Check:**
```json
{"name": "Updated Homepage Check", "frequency": 600}
