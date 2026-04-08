---
name: cloudflaredns-domains
description: Manage Cloudflare DNS zones and records. Use when the user mentions cloudflare,
  DNS, zone, domain, record.
version: 1.0.0
skill_type: external
base_url_env: CLOUDFLARE_DNS_BASE_URL
auth_env_var: CLOUDFLARE_API_TOKEN
auth_type: bearer
triggers:
  - cloudflare
  - DNS
  - zone
  - domain
  - record
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires CLOUDFLARE_DNS_BASE_URL and CLOUDFLARE_API_TOKEN environment
  variables.
---

# Cloudflaredns-Domains

Manage Cloudflare DNS zones and records. Use when the user mentions cloudflare, DNS, zone, domain, record.

## API Endpoints

- **GET** `/client/v4/zones` - List zones
- **GET** `/client/v4/zones/{zoneId}` - Get a zone
- **POST** `/client/v4/zones` - Create a zone
- **DELETE** `/client/v4/zones/{zoneId}` - Delete a zone
- **GET** `/client/v4/zones/{zoneId}/dns_records` - List DNS records
- **POST** `/client/v4/zones/{zoneId}/dns_records` - Create a DNS record
- **PUT** `/client/v4/zones/{zoneId}/dns_records/{recordId}` - Update a DNS record
- **DELETE** `/client/v4/zones/{zoneId}/dns_records/{recordId}` - Delete a DNS record
- **POST** `/client/v4/zones/{zoneId}/purge_cache` - Purge cache
- **GET** `/client/v4/user` - Get current user

## Actions

- list: List zones (GET /client/v4/zones)
- get_by_id: Get a zone (GET /client/v4/zones/{zoneId})
- create: Create a zone (POST /client/v4/zones)
- delete: Delete a zone (DELETE /client/v4/zones/{zoneId})
- list_dns_records: List DNS records (GET /client/v4/zones/{zoneId}/dns_records)
- create_dns_records: Create a DNS record (POST /client/v4/zones/{zoneId}/dns_records)
- update: Update a DNS record (PUT /client/v4/zones/{zoneId}/dns_records/{recordId})
- delete_dns_records: Delete a DNS record (DELETE /client/v4/zones/{zoneId}/dns_records/{recordId})
- create_purge_cache: Purge cache (POST /client/v4/zones/{zoneId}/purge_cache)
- list_user: Get current user (GET /client/v4/user)

## Fields

- `name`: string [REQUIRED for create zone/record]
- `type`: string [REQUIRED for DNS record] ("A", "AAAA", "CNAME", "MX", "TXT", "NS")
- `content`: string [REQUIRED for DNS record] (IP address, hostname, etc.)
- `ttl`: integer [OPTIONAL] (1 = auto)
- `proxied`: boolean [OPTIONAL]

## Example Request Bodies

**Create a DNS Zone:**
```json
{
  "name": "example.com",
  "type": "full"
}
```

**Create a DNS Record:**
```json
{
  "type": "A",
  "name": "api.example.com",
  "content": "203.0.113.50",
  "ttl": 3600,
  "proxied": true
}
```
