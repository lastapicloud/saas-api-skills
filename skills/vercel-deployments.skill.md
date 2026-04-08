---
name: vercel-deployments
description: Manage deployments, projects, and domains in Vercel. Use when the user
  mentions vercel, deployment, deploy, domain, project, serverless.
version: 1.0.0
skill_type: external
base_url_env: VERCEL_BASE_URL
auth_env_var: VERCEL_ACCESS_TOKEN
auth_type: bearer
triggers:
  - vercel
  - deployment
  - deploy
  - domain
  - project
  - serverless
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires VERCEL_BASE_URL and VERCEL_ACCESS_TOKEN environment variables.
---

# Vercel-Deployments

Manage deployments, projects, and domains in Vercel. Use when the user mentions vercel, deployment, deploy, domain, project, serverless.

## API Endpoints

- **GET** `/v6/deployments` - List deployments
- **GET** `/v13/deployments/{id}` - Get a deployment
- **POST** `/v13/deployments` - Create a deployment
- **DELETE** `/v13/deployments/{id}` - Delete a deployment
- **GET** `/v10/projects` - List projects
- **GET** `/v10/projects/{idOrName}` - Get a project
- **GET** `/v6/domains` - List domains
- **POST** `/v6/domains` - Add a domain
- **GET** `/v1/drains` - Retrieve a list of all Drains
- **POST** `/v1/drains` - Create a new Drain
- **PATCH** `/v1/drains/{id}` - Update an existing Drain
- **DELETE** `/v1/drains/{id}` - Delete a drain
- **GET** `/v5/domains` - List all the domains
- **POST** `/v7/domains` - Add an existing domain to the Vercel platform
- **PATCH** `/v3/domains/{domain}` - Update or move apex domain

## Actions

- list: List deployments (GET /v6/deployments)
- get_by_id: Get a deployment (GET /v13/deployments/{id})
- create: Create a deployment (POST /v13/deployments)
- delete: Delete a deployment (DELETE /v13/deployments/{id})
- list_projects: List projects (GET /v10/projects)
- get_by_id_projects: Get a project (GET /v10/projects/{idOrName})
- list_domains: List domains (GET /v6/domains)
- create_domains: Add a domain (POST /v6/domains)
- list_drains: Retrieve a list of all Drains (GET /v1/drains)
- create_drains: Create a new Drain (POST /v1/drains)
- update: Update an existing Drain (PATCH /v1/drains/{id})
- delete_drains: Delete a drain (DELETE /v1/drains/{id})
- list_domains_2: List all the domains (GET /v5/domains)
- create_domains_2: Add an existing domain to the Vercel platform (POST /v7/domains)
- update_domains: Update or move apex domain (PATCH /v3/domains/{domain})

## Fields

- `id`: string [REQUIRED for get/delete deployment] (deployment ID)
- `idOrName`: string [REQUIRED for get_project] (project ID or name)
- `name`: string [REQUIRED for create_deployment] (project name)
- `gitSource`: object [OPTIONAL for create_deployment] (Git source with type, repo, ref)
- `target`: string [OPTIONAL for create_deployment] (production or preview)
- `teamId`: string [OPTIONAL] (team ID as query param for team resources)
- `limit`: integer [OPTIONAL] (results per page)
- `since`: integer [OPTIONAL for list_deployments] (UNIX timestamp filter)
- `domain`: string [REQUIRED for add_domain] (domain name to add)

## Example Request Bodies

**Create Deployment:**
```json
{"name": "my-project", "gitSource": {"type": "github", "repo": "user/repo", "ref": "main"}, "target": "production"}
```

**Add Domain:**
```json
{"name": "example.com"}
```

**List Deployments (Query Params):**
Query parameter: `limit=20&target=production&teamId=team_abc123`
