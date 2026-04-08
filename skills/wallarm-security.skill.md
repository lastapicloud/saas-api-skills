---
name: wallarm-security
description: Manage Wallarm WAF/API security attacks and rules. Use when the user
  mentions wallarm, WAF, API security, attack, rule.
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
- create_delete: Delete a rule (POST /v1/objects/rule/delete)
- list_rule: List rules (GET /v1/objects/rule)
- list_node: List nodes (GET /v2/node)
- list_user: Get current user (GET /v1/user)
- list_events: List events (GET /v2/events)

## Fields

- `filter`: object [REQUIRED for search attacks]
- `type`: string [REQUIRED for create rule]
- `action`: object [REQUIRED for create rule]
- `point`: array [OPTIONAL for create rule]

## Example Request Bodies

**Search Attacks:**
```json
{"filter": {"time": [["2026-03-01", "2026-03-24"]], "type": ["sqli", "xss"]}}
```

**Create Rule:**
```json
{"type": "ignore", "action": {"type": "iequal", "value": "/api/health"}, "point": [["path"]]}
```
