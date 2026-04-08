---
name: saltsecurity-api
description: Manage Salt Security API discovery and threat protection. Use when the
  user mentions salt security, salt, API security, API discovery, threat.
version: 1.0.0
skill_type: external
base_url_env: SALTSECURITY_BASE_URL
auth_env_var: SALTSECURITY_API_TOKEN
auth_type: bearer
triggers:
  - salt security
  - salt
  - API security
  - API discovery
  - threat
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires SALTSECURITY_BASE_URL and SALTSECURITY_API_TOKEN environment
  variables.
---

# Saltsecurity-Api

Manage Salt Security API discovery and threat protection. Use when the user mentions salt security, salt, API security, API discovery, threat.

## API Endpoints

- **GET** `/api/v1/apis` - List discovered APIs
- **GET** `/api/v1/apis/{apiId}` - Get API details
- **GET** `/api/v1/alerts` - List security alerts
- **GET** `/api/v1/alerts/{alertId}` - Get alert details
- **PUT** `/api/v1/alerts/{alertId}` - Update alert status
- **GET** `/api/v1/attackers` - List attackers
- **GET** `/api/v1/vulnerabilities` - List vulnerabilities
- **GET** `/api/v1/endpoints` - List API endpoints
- **GET** `/api/v1/tokens` - List API tokens
- **GET** `/api/v1/stats` - Get statistics

## Actions

- list: List discovered APIs (GET /api/v1/apis)
- get_by_id: Get API details (GET /api/v1/apis/{apiId})
- list_alerts: List security alerts (GET /api/v1/alerts)
- get_by_id_alerts: Get alert details (GET /api/v1/alerts/{alertId})
- update: Update alert status (PUT /api/v1/alerts/{alertId})
- list_attackers: List attackers (GET /api/v1/attackers)
- list_vulnerabilities: List vulnerabilities (GET /api/v1/vulnerabilities)
- list_endpoints: List API endpoints (GET /api/v1/endpoints)
- list_tokens: List API tokens (GET /api/v1/tokens)
- list_stats: Get statistics (GET /api/v1/stats)

## Fields

- `status`: string [REQUIRED for update alert] (e.g., "open", "acknowledged", "resolved")
- `filter`: object [OPTIONAL for list queries]

## Example Request Bodies

**Update Alert Status:**
```json
{"status": "acknowledged"}
```

**List APIs with Filter:**
```json
{"filter": {"status": "active"}}
