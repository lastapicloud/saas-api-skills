---
name: porkbun-domains
description: Manage domains and DNS via Porkbun. Use when the user mentions porkbun,
  domain, dns, registrar.
version: 1.0.0
skill_type: external
base_url_env: PORKBUN_BASE_URL
auth_env_var: PORKBUN_API_KEY
auth_user_env: PORKBUN_SECRET_API_KEY
auth_type: header
triggers:
  - porkbun
  - domain
  - dns
  - registrar
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires PORKBUN_BASE_URL and PORKBUN_API_KEY environment variables.
---

# Porkbun-Domains

Manage domains and DNS via Porkbun. Use when the user mentions porkbun, domain, dns, registrar.

## API Endpoints

- **POST** `/api/json/v3/domain/listAll` - List domains
- **POST** `/api/json/v3/dns/retrieve/{domain}` - List DNS records
- **POST** `/api/json/v3/dns/create/{domain}` - Create DNS record
- **POST** `/api/json/v3/dns/edit/{domain}/{id}` - Edit DNS record
- **POST** `/api/json/v3/dns/delete/{domain}/{id}` - Delete DNS record
- **POST** `/api/json/v3/pricing/get` - Get pricing
- **POST** `/api/json/v3/domain/getNs/{domain}` - Get nameservers

## Actions

- create: List domains (POST /api/json/v3/domain/listAll)
- add_retrieve: List DNS records (POST /api/json/v3/dns/retrieve/{domain})
- add_create: Create DNS record (POST /api/json/v3/dns/create/{domain})
- add_edit: Edit DNS record (POST /api/json/v3/dns/edit/{domain}/{id})
- add_delete: Delete DNS record (POST /api/json/v3/dns/delete/{domain}/{id})
- create_get: Get pricing (POST /api/json/v3/pricing/get)
- add_getns: Get nameservers (POST /api/json/v3/domain/getNs/{domain})

## Fields

- `type`: string [REQUIRED for create] (A, CNAME, etc.)
- `content`: string [REQUIRED for create]
- `name`: string [OPTIONAL]
- `ttl`: integer [OPTIONAL]

## Example Request Bodies

**Create a DNS Record:**
```json
{
  "type": "A",
  "content": "198.51.100.42",
  "name": "www",
  "ttl": 600
}
```

**Edit a DNS Record:**
```json
{
  "type": "A",
  "content": "198.51.100.99",
  "ttl": 300
}
```
