---
name: wallarm-security
description: 'Manage Wallarm WAF/API security attacks and rules. Use when the user
  mentions wallarm, WAF, API security, attack, rule.

  '
version: 1.0.0
skill_type: external
base_url_env: WALLARM_BASE_URL
auth_env_var: WALLARM_API_TOKEN
auth_type: header
triggers:
  - wallarm
  - WAF
  - API security
  - attack
  - rule
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires WALLARM_BASE_URL and WALLARM_API_TOKEN environment variables.
annotations:
  readOnlyHint: false
  destructiveHint: false
  idempotentHint: false
---

# Wallarm-Security

Manage Wallarm WAF/API security attacks and rules. Use when the user mentions wallarm, WAF, API security, attack, rule.


## API Endpoints

- **POST** `/v2/search/attacks` - Search attacks
- **GET** `/v2/hit` - List hits
- **POST** `/v1/objects/rule/create` - Create a rule
- **POST** `/v1/objects/rule/delete` - Delete a rule
- **GET** `/v1/objects/rule` - List rules
- **GET** `/v2/node` - List nodes
- **GET** `/v1/user` - Get current user
- **GET** `/v2/events` - List events

## Actions

- create: Search attacks (POST /v2/search/attacks)
- list: List hits (GET /v2/hit)
- create_rule: Create a rule (POST /v1/objects/rule/create)
- delete_rule: Delete a rule (POST /v1/objects/rule/delete)
- list_rules: List rules (GET /v1/objects/rule)
- list_nodes: List nodes (GET /v2/node)
- get_current_user: Get current user (GET /v1/user)
- list_events: List events (GET /v2/events)

## Fields

- `filter`: object [REQUIRED for search attacks] — Filter criteria
- `type`: string [REQUIRED for create rule] — Resource type
- `action`: object [REQUIRED for create rule] — Action configuration
- `point`: array [OPTIONAL for create rule] — List of point

## Example Request Bodies

**Search Attacks:**
```json
{"filter": {"time": [["2026-03-01", "2026-03-24"]], "type": ["sqli", "xss"]}}
```

**Create Rule:**
```json
{"type": "ignore", "action": {"type": "iequal", "value": "/api/health"}, "point": [["path"]]}
```

## Response

**Attack object:**
- `id`: string — Unique attack identifier
- `name`: string — Attack name or title
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
