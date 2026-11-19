---
name: googledns-domains
description: 'Manage Google Cloud DNS zones and records. Use when the user mentions
  google cloud dns, google dns, DNS, zone, record.

  '
version: 1.0.0
skill_type: external
base_url_env: GOOGLE_CLOUD_DNS_BASE_URL
auth_env_var: GOOGLE_API_TOKEN
auth_type: bearer
triggers:
  - google cloud dns
  - google dns
  - DNS
  - zone
  - record
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires GOOGLE_CLOUD_DNS_BASE_URL and GOOGLE_API_TOKEN environment
  variables.
annotations:
  readOnlyHint: false
  destructiveHint: true
  idempotentHint: false
---

# Googledns-Domains

Manage Google Cloud DNS zones and records. Use when the user mentions google cloud dns, google dns, DNS, zone, record.


## API Endpoints

- **GET** `/dns/v1/projects/{project}/managedZones` - List zones
- **GET** `/dns/v1/projects/{project}/managedZones/{zoneId}` - Get a zone
- **POST** `/dns/v1/projects/{project}/managedZones` - Create a zone
- **DELETE** `/dns/v1/projects/{project}/managedZones/{zoneId}` - Delete a zone
- **GET** `/dns/v1/projects/{project}/managedZones/{zoneId}/rrsets` - List record sets
- **POST** `/dns/v1/projects/{project}/managedZones/{zoneId}/changes` - Create a change (add/remove records)
- **GET** `/dns/v1/projects/{project}/managedZones/{zoneId}/changes` - List changes

## Actions

- list: List zones (GET /dns/v1/projects/{project}/managedZones)
- get_by_id: Get a zone (GET /dns/v1/projects/{project}/managedZones/{zoneId})
- create: Create a zone (POST /dns/v1/projects/{project}/managedZones)
- delete: Delete a zone (DELETE /dns/v1/projects/{project}/managedZones/{zoneId})
- list_record_sets: List record sets (GET /dns/v1/projects/{project}/managedZones/{zoneId}/rrsets)
- create_change_addremove_records: Create a change (add/remove records) (POST /dns/v1/projects/{project}/managedZones/{zoneId}/changes)
- list_changes: List changes (GET /dns/v1/projects/{project}/managedZones/{zoneId}/changes)

## Fields

- `name`: string [REQUIRED for create zone] (DNS name, e.g., "example.com.") — Display name
- `dnsName`: string [REQUIRED for create zone] — Dns display name
- `description`: string [OPTIONAL] — Human-readable description
- `additions`: array [OPTIONAL for change] with `name`, `type`, `rrdatas`, `ttl` — List of additions
- `deletions`: array [OPTIONAL for change] — List of deletions

## Example Request Bodies

**Create Zone:**
```json
{"name": "example-zone", "dnsName": "example.com.", "description": "Production DNS zone"}
```

**Create Change (Add Record):**
```json
{"additions": [{"name": "app.example.com.", "type": "A", "rrdatas": ["93.184.216.34"], "ttl": 300}]}
```

## Response

**Managedzone object:**
- `id`: string — Unique managedzone identifier
- `name`: string — Managedzone name or title
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
