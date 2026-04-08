---
name: gitguardian-security
description: Detect and manage secret leaks via GitGuardian. Use when the user mentions
  gitguardian, secret, leak, security, scanning.
version: 1.0.0
skill_type: external
base_url_env: GITGUARDIAN_BASE_URL
auth_env_var: GITGUARDIAN_API_TOKEN
auth_type: header
triggers:
  - gitguardian
  - secret
  - leak
  - security
  - scanning
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires GITGUARDIAN_BASE_URL and GITGUARDIAN_API_TOKEN environment
  variables.
---

# Gitguardian-Security

Detect and manage secret leaks via GitGuardian. Use when the user mentions gitguardian, secret, leak, security, scanning.

## API Endpoints

- **GET** `/v1/incidents/secrets` - List secret incidents
- **GET** `/v1/incidents/secrets/{incident_id}` - Get incident
- **PATCH** `/v1/incidents/secrets/{incident_id}` - Update incident
- **POST** `/v1/scan` - Scan content for secrets
- **GET** `/v1/members` - List members
- **GET** `/v1/sources` - List sources
- **GET** `/v1/health` - Health check

## Actions

- list: List secret incidents (GET /v1/incidents/secrets)
- get_by_id: Get incident (GET /v1/incidents/secrets/{incident_id})
- update: Update incident (PATCH /v1/incidents/secrets/{incident_id})
- create: Scan content for secrets (POST /v1/scan)
- list_members: List members (GET /v1/members)
- list_sources: List sources (GET /v1/sources)
- list_health: Health check (GET /v1/health)

## Fields

- `status`: string [OPTIONAL] (open, resolved, ignored)
- `document`: string [REQUIRED for scan]
- `filename`: string [OPTIONAL for scan]

## Example Request Bodies

**Scan Content:**
```json
{"document": "API_KEY=sk_live_abc123def456", "filename": "config.py"}
```

**Update Incident:**
```json
{"status": "resolved"}
