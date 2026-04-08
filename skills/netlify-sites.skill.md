---
name: netlify-sites
description: Manage sites, deploys, and DNS in Netlify. Use when the user mentions
  netlify, site, deploy, DNS, build, hosting.
version: 1.0.0
skill_type: external
base_url_env: NETLIFY_BASE_URL
auth_env_var: NETLIFY_ACCESS_TOKEN
auth_type: bearer
triggers:
  - netlify
  - site
  - deploy
  - DNS
  - build
  - hosting
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires NETLIFY_BASE_URL and NETLIFY_ACCESS_TOKEN environment variables.
---

# Netlify-Sites

Manage sites, deploys, and DNS in Netlify. Use when the user mentions netlify, site, deploy, DNS, build, hosting.

## API Endpoints

- **GET** `/sites` - List sites
- **POST** `/sites` - Create a site
- **GET** `/sites/{site_id}` - Get a site
- **PATCH** `/sites/{site_id}` - Update a site
- **DELETE** `/sites/{site_id}` - Delete a site
- **GET** `/sites/{site_id}/deploys` - List deploys for a site
- **POST** `/sites/{site_id}/deploys` - Create a deploy
- **GET** `/sites/{site_id}/deploys/{deploy_id}` - Get a deploy
- **POST** `/api/v1/sites` - Now you have a site ID and you can create a new deploy, either with a file digest or a ZIP file.
- **POST** `/api/v1/sites/{site_id}/deploys`
- **PUT** `/api/v1/deploys/{deploy_id}/files/index.html`
- **PUT** `/api/v1/deploys/{deploy_id}/functions/hello-world` - Possible runtime parameters are:
- **GET** `/api/v1/sites/{site_id}/deploys/{deploy_id}` - You can check the state parameter in the response. It will be set to preparing as the upload manifest is generated, and
- **GET** `/api/v1/deploys/{deploy_id}`
- **GET** `/api/v1/sites`

## Actions

- list: List sites (GET /sites)
- create: Create a site (POST /sites)
- get_by_id: Get a site (GET /sites/{site_id})
- update: Update a site (PATCH /sites/{site_id})
- delete: Delete a site (DELETE /sites/{site_id})
- list_deploys: List deploys for a site (GET /sites/{site_id}/deploys)
- create_deploys: Create a deploy (POST /sites/{site_id}/deploys)
- get_by_id_deploys: Get a deploy (GET /sites/{site_id}/deploys/{deploy_id})
- create_sites: Now you have a site ID and you can create a new deploy, either with a file diges (POST /api/v1/sites)
- create_deploys_2: POST /api/v1/sites/{site_id}/deploys (POST /api/v1/sites/{site_id}/deploys)
- put_index.html: PUT /api/v1/deploys/{deploy_id}/files/index.html (PUT /api/v1/deploys/{deploy_id}/files/index.html)
- put_hello_world: Possible runtime parameters are: (PUT /api/v1/deploys/{deploy_id}/functions/hello-world)
- get_by_id_deploys_2: You can check the state parameter in the response. It will be set to preparing a (GET /api/v1/sites/{site_id}/deploys/{deploy_id})
- get_by_id_deploys_3: GET /api/v1/deploys/{deploy_id} (GET /api/v1/deploys/{deploy_id})
- list_sites: GET /api/v1/sites (GET /api/v1/sites)

## Fields

- `site_id`: string [REQUIRED for site-scoped actions] (site ID)
- `deploy_id`: string [REQUIRED for get_deploy] (deploy ID)
- `name`: string [OPTIONAL for create_site] (site subdomain name)
- `custom_domain`: string [OPTIONAL for create_site] (custom domain)
- `repo`: object [OPTIONAL for create_site] (repository link with provider, repo_path, branch)
- `branch`: string [OPTIONAL for create_deploy] (branch to deploy)
- `title`: string [OPTIONAL for create_deploy] (deploy title/message)
- `page`: integer [OPTIONAL] (page number)
- `per_page`: integer [OPTIONAL] (results per page)

## Example Request Bodies

**Create Site:**
```json
{"name": "my-awesome-site", "repo": {"provider": "github", "repo_path": "user/repo", "branch": "main"}}
```

**Update Site:**
```json
{"custom_domain": "www.example.com"}
```

**Create Deploy:**
```json
{"branch": "main", "title": "Production release v1.2.0"}
```
