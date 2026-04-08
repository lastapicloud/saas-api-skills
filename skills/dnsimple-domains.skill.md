---
name: dnsimple-domains
description: Manage DNSimple domains, records, and certificates. Use when the user
  mentions dnsimple, domain, DNS, record, certificate.
version: 1.0.0
skill_type: external
base_url_env: DNSIMPLE_BASE_URL
auth_env_var: DNSIMPLE_ACCESS_TOKEN
auth_type: bearer
triggers:
  - dnsimple
  - domain
  - DNS
  - record
  - certificate
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires DNSIMPLE_BASE_URL and DNSIMPLE_ACCESS_TOKEN environment variables.
---

# Dnsimple-Domains

Manage DNSimple domains, records, and certificates. Use when the user mentions dnsimple, domain, DNS, record, certificate.

## API Endpoints

- **GET** `/v2/{accountId}/domains` - List domains
- **GET** `/v2/{accountId}/domains/{domainId}` - Get a domain
- **POST** `/v2/{accountId}/domains` - Create a domain
- **DELETE** `/v2/{accountId}/domains/{domainId}` - Delete a domain
- **GET** `/v2/{accountId}/zones/{zoneName}/records` - List DNS records
- **POST** `/v2/{accountId}/zones/{zoneName}/records` - Create a DNS record
- **PATCH** `/v2/{accountId}/zones/{zoneName}/records/{recordId}` - Update a DNS record
- **DELETE** `/v2/{accountId}/zones/{zoneName}/records/{recordId}` - Delete a DNS record
- **GET** `/v2/{accountId}/domains/{domainId}/certificates` - List certificates
- **GET** `/v2/whoami` - Get current identity

## Actions

- list: List domains (GET /v2/{accountId}/domains)
- get_by_id: Get a domain (GET /v2/{accountId}/domains/{domainId})
- create: Create a domain (POST /v2/{accountId}/domains)
- delete: Delete a domain (DELETE /v2/{accountId}/domains/{domainId})
- list_records: List DNS records (GET /v2/{accountId}/zones/{zoneName}/records)
- create_records: Create a DNS record (POST /v2/{accountId}/zones/{zoneName}/records)
- update: Update a DNS record (PATCH /v2/{accountId}/zones/{zoneName}/records/{recordId})
- delete_records: Delete a DNS record (DELETE /v2/{accountId}/zones/{zoneName}/records/{recordId})
- list_certificates: List certificates (GET /v2/{accountId}/domains/{domainId}/certificates)
- list_whoami: Get current identity (GET /v2/whoami)

## Fields

- `name`: string [REQUIRED for create domain/record]
- `type`: string [REQUIRED for record] ("A", "AAAA", "CNAME", "MX", "TXT")
- `content`: string [REQUIRED for record]
- `ttl`: integer [OPTIONAL]
- `priority`: integer [OPTIONAL for MX]

## Example Request Bodies

**Create Domain:**
```json
{"name": "example-app.com"}
```

**Create DNS Record:**
```json
{"name": "api", "type": "A", "content": "203.0.113.50", "ttl": 3600}
```
