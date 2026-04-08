---
name: adobe-cc
description: Manage Adobe Creative Cloud assets and libraries. Use when the user mentions
  adobe, creative cloud, photoshop, illustrator, asset, library.
version: 1.0.0
skill_type: external
base_url_env: ADOBE_CC_BASE_URL
auth_env_var: ADOBE_CC_ACCESS_TOKEN
auth_type: bearer
triggers:
  - adobe
  - creative cloud
  - photoshop
  - illustrator
  - asset
  - library
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires ADOBE_CC_BASE_URL and ADOBE_CC_ACCESS_TOKEN environment variables.
---

# Adobe-Cc

Manage Adobe Creative Cloud assets and libraries. Use when the user mentions adobe, creative cloud, photoshop, illustrator, asset, library.

## API Endpoints

- **GET** `/v1/assets` - List assets
- **GET** `/v1/assets/{assetId}` - Get asset by ID
- **POST** `/v1/assets` - Upload an asset
- **DELETE** `/v1/assets/{assetId}` - Delete an asset
- **GET** `/v1/libraries` - List libraries
- **POST** `/v1/libraries` - Create a library
- **GET** `/v1/libraries/{libraryId}/elements` - List library elements
- **POST** `/v1/libraries/{libraryId}/elements` - Add element to library
- **GET** `/bin/querybuilder.json`
- **POST** `/bin/querybuilder.json`
- **GET** `/{path}/{name}`
- **DELETE** `/{path}/{name}`
- **POST** `/{path}/{name}`
- **GET** `/etc/truststore/truststore.p12`
- **POST** `/etc/truststore`

## Actions

- list: List assets (GET /v1/assets)
- get_by_id: Get asset by ID (GET /v1/assets/{assetId})
- create: Upload an asset (POST /v1/assets)
- delete: Delete an asset (DELETE /v1/assets/{assetId})
- list_libraries: List libraries (GET /v1/libraries)
- create_libraries: Create a library (POST /v1/libraries)
- list_elements: List library elements (GET /v1/libraries/{libraryId}/elements)
- create_elements: Add element to library (POST /v1/libraries/{libraryId}/elements)
- query: GET /bin/querybuilder.json (GET /bin/querybuilder.json)
- query_querybuilder_json: POST /bin/querybuilder.json (POST /bin/querybuilder.json)
- get_by_id_resource: GET /{path}/{name} (GET /{path}/{name})
- delete_resource: DELETE /{path}/{name} (DELETE /{path}/{name})
- create_resource: POST /{path}/{name} (POST /{path}/{name})
- list_truststore_p12: GET /etc/truststore/truststore.p12 (GET /etc/truststore/truststore.p12)
- create_truststore: POST /etc/truststore (POST /etc/truststore)

## Fields

- `name`: string [REQUIRED for create]
- `type`: string [OPTIONAL] (asset type)
- `libraryId`: string [OPTIONAL]

## Example Request Bodies

**Upload Asset:**
```json
{"name": "hero-banner.psd", "type": "image", "libraryId": "lib-abc123"}
```

**Create Library:**
```json
{"name": "Brand Assets Q2 2026"}
```
