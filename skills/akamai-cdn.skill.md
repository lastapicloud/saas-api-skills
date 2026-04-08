---
name: akamai-cdn
description: Manage CDN configurations and purge cache via Akamai. Use when the user
  mentions akamai, cdn, cache, purge, edge, delivery.
version: 1.0.0
skill_type: external
base_url_env: AKAMAI_BASE_URL
auth_env_var: AKAMAI_ACCESS_TOKEN
auth_type: header
triggers:
  - akamai
  - cdn
  - cache
  - purge
  - edge
  - delivery
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires AKAMAI_BASE_URL and AKAMAI_ACCESS_TOKEN environment variables.
---

# Akamai-Cdn

Manage CDN configurations and purge cache via Akamai. Use when the user mentions akamai, cdn, cache, purge, edge, delivery.

## API Endpoints

- **GET** `/papi/v1/properties` - List properties
- **GET** `/papi/v1/properties/{propertyId}` - Get property details
- **POST** `/papi/v1/properties` - Create a property
- **POST** `/ccu/v3/invalidate/url/production` - Purge cache by URL
- **POST** `/ccu/v3/invalidate/cpcode/production` - Purge cache by CP code
- **GET** `/papi/v1/properties/{propertyId}/versions` - List property versions
- **POST** `/papi/v1/properties/{propertyId}/activations` - Activate a property version
- **GET** `/papi/v1/groups` - List groups

## Actions

- list: List properties (GET /papi/v1/properties)
- get_by_id: Get property details (GET /papi/v1/properties/{propertyId})
- create: Create a property (POST /papi/v1/properties)
- create_production: Purge cache by URL (POST /ccu/v3/invalidate/url/production)
- create_production_2: Purge cache by CP code (POST /ccu/v3/invalidate/cpcode/production)
- list_versions: List property versions (GET /papi/v1/properties/{propertyId}/versions)
- create_activations: Activate a property version (POST /papi/v1/properties/{propertyId}/activations)
- list_groups: List groups (GET /papi/v1/groups)

## Fields

- `propertyName`: string [REQUIRED for create]
- `productId`: string [REQUIRED for create]
- `objects`: array [REQUIRED for purge] (URLs or CP codes)

## Example Request Bodies

**Create Property:**
```json
{"propertyName": "www.example.com", "productId": "prd_Web_Accel", "ruleFormat": "latest"}
```

**Purge Cache by URL:**
```json
{"objects": ["https://www.example.com/images/logo.png", "https://www.example.com/css/main.css"]}
```
