---
name: heroku-apps
description: Manage apps, dynos, and addons via Heroku. Use when the user mentions
  heroku, app, dyno, addon, deploy, platform.
version: 1.0.0
skill_type: external
base_url_env: HEROKU_BASE_URL
auth_env_var: HEROKU_API_TOKEN
auth_type: bearer
triggers:
  - heroku
  - app
  - dyno
  - addon
  - deploy
  - platform
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires HEROKU_BASE_URL and HEROKU_API_TOKEN environment variables.
---

# Heroku-Apps

Manage apps, dynos, and addons via Heroku. Use when the user mentions heroku, app, dyno, addon, deploy, platform.

## API Endpoints

- **GET** `/apps` - List apps
- **POST** `/apps` - Create app
- **GET** `/apps/{app_id_or_name}` - Get app
- **DELETE** `/apps/{app_id_or_name}` - Delete app
- **GET** `/apps/{app_id_or_name}/dynos` - List dynos
- **POST** `/apps/{app_id_or_name}/dynos` - Restart dynos
- **GET** `/apps/{app_id_or_name}/addons` - List addons
- **GET** `/apps/{app_id_or_name}/releases` - List releases
- **GET** `/{country}` - Returns all regions present in Tanzania
- **GET** `/{country}/{region}` - Returns all districts in region
- **GET** `/{country}/{region}/{district}` - Returns all wards in a district
- **GET** `/{country}/{region}/{district}/{ward}` - Returns all streets in a ward
- **GET** `/{country}/{region}/{district}/{ward}/{street}` - Returns all neighborhood in a street
- **POST** `/v1/file` - Faz o upload de um arquivo
- **GET** `/v1/file/{fileId}` - Retorna as informações básicas de um arquivo previamente processado

## Actions

- list: List apps (GET /apps)
- create: Create app (POST /apps)
- get_by_id: Get app (GET /apps/{app_id_or_name})
- delete: Delete app (DELETE /apps/{app_id_or_name})
- list_dynos: List dynos (GET /apps/{app_id_or_name}/dynos)
- create_dynos: Restart dynos (POST /apps/{app_id_or_name}/dynos)
- list_addons: List addons (GET /apps/{app_id_or_name}/addons)
- list_releases: List releases (GET /apps/{app_id_or_name}/releases)
- get_by_id_resource: Returns all regions present in Tanzania (GET /{country})
- get_by_id_resource_2: Returns all districts in region (GET /{country}/{region})
- get_by_id_resource_3: Returns all wards in a district (GET /{country}/{region}/{district})
- get_by_id_resource_4: Returns all streets in a ward (GET /{country}/{region}/{district}/{ward})
- get_by_id_resource_5: Returns all neighborhood in a street (GET /{country}/{region}/{district}/{ward}/{street})
- create_file: Faz o upload de um arquivo (POST /v1/file)
- get_by_id_file: Retorna as informações básicas de um arquivo previamente processado (GET /v1/file/{fileId})

## Fields

- `name`: string [OPTIONAL for create]
- `region`: string [OPTIONAL]
- `stack`: string [OPTIONAL]

## Example Request Bodies

**Create App:**
```json
{"name": "my-web-app", "region": "us", "stack": "heroku-22"}
```

**Restart Dynos:**
```json
{"type": "web"}
```
