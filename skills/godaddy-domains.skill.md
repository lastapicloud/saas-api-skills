---
name: godaddy-domains
description: Manage domains and DNS via GoDaddy. Use when the user mentions godaddy,
  domain, dns, registrar, whois.
version: 1.0.0
skill_type: external
base_url_env: GODADDY_BASE_URL
auth_env_var: GODADDY_API_KEY
auth_user_env: GODADDY_API_SECRET
auth_type: header
triggers:
  - godaddy
  - domain
  - dns
  - registrar
  - whois
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires GODADDY_BASE_URL and GODADDY_API_KEY environment variables.
---

# Godaddy-Domains

Manage domains and DNS via GoDaddy. Use when the user mentions godaddy, domain, dns, registrar, whois.

## API Endpoints

- **GET** `/v1/domains` - List domains
- **GET** `/v1/domains/{domain}` - Get domain
- **POST** `/v1/domains/purchase` - Purchase domain
- **GET** `/v1/domains/available` - Check availability
- **GET** `/v1/domains/{domain}/records` - List DNS records
- **PUT** `/v1/domains/{domain}/records` - Replace DNS records
- **PATCH** `/v1/domains/{domain}/records` - Update DNS records
- **DELETE** `/v1/domains/{domain}/records/{type}/{name}` - Delete DNS record
- **GET** `/v1/countries` - Retrieves summary country information for the provided marketId and filters
- **GET** `/v1/countries/{countryKey}` - Retrieves country and summary state information for provided countryKey
- **GET** `/v1/subscriptions` - Retrieve a list of Subscriptions for the specified Shopper
- **GET** `/v1/subscriptions/productGroups` - Retrieve a list of ProductGroups for the specified Shopper
- **PATCH** `/v1/subscriptions/{subscriptionId}` - Update details for the specified Subscription
- **GET** `/v1/subscriptions/{subscriptionId}` - Retrieve details for the specified Subscription
- **DELETE** `/v1/subscriptions/{subscriptionId}` - Cancel the specified Subscription

## Actions

- list: List domains (GET /v1/domains)
- get_by_id: Get domain (GET /v1/domains/{domain})
- create: Purchase domain (POST /v1/domains/purchase)
- list_available: Check availability (GET /v1/domains/available)
- list_records: List DNS records (GET /v1/domains/{domain}/records)
- put_records: Replace DNS records (PUT /v1/domains/{domain}/records)
- patch_records: Update DNS records (PATCH /v1/domains/{domain}/records)
- delete: Delete DNS record (DELETE /v1/domains/{domain}/records/{type}/{name})
- list_countries: Retrieves summary country information for the provided marketId and filters (GET /v1/countries)
- get_by_id_countries: Retrieves country and summary state information for provided countryKey (GET /v1/countries/{countryKey})
- list_subscriptions: Retrieve a list of Subscriptions for the specified Shopper (GET /v1/subscriptions)
- list_productgroups: Retrieve a list of ProductGroups for the specified Shopper (GET /v1/subscriptions/productGroups)
- update: Update details for the specified Subscription (PATCH /v1/subscriptions/{subscriptionId})
- get_by_id_subscriptions: Retrieve details for the specified Subscription (GET /v1/subscriptions/{subscriptionId})
- delete_subscriptions: Cancel the specified Subscription (DELETE /v1/subscriptions/{subscriptionId})

## Fields

- `domain`: string [REQUIRED]
- `type`: string [OPTIONAL for records] (A, CNAME, etc.)
- `data`: string [REQUIRED for records]
- `ttl`: integer [OPTIONAL]

## Example Request Bodies

**Purchase Domain:**
```json
{"domain": "mywebsite.com", "consent": {"agreementKeys": ["DNRA"], "agreedBy": "192.168.1.1", "agreedAt": "2024-01-15T10:00:00Z"}}
```

**Update DNS Records:**
```json
[{"type": "A", "name": "@", "data": "93.184.216.34", "ttl": 3600}]
```
