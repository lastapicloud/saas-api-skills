---
name: digitalocean-droplets
description: Manage DigitalOcean droplets, domains, and databases. Use when the user
  mentions digitalocean, droplet, domain, database, kubernetes.
version: 1.0.0
skill_type: external
base_url_env: DIGITALOCEAN_BASE_URL
auth_env_var: DIGITALOCEAN_API_TOKEN
auth_type: bearer
triggers:
  - digitalocean
  - droplet
  - domain
  - database
  - kubernetes
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires DIGITALOCEAN_BASE_URL and DIGITALOCEAN_API_TOKEN environment
  variables.
---

# Digitalocean-Droplets

Manage DigitalOcean droplets, domains, and databases. Use when the user mentions digitalocean, droplet, domain, database, kubernetes.

## API Endpoints

- **GET** `/v2/droplets` - List droplets
- **GET** `/v2/droplets/{dropletId}` - Get a droplet
- **POST** `/v2/droplets` - Create a droplet
- **DELETE** `/v2/droplets/{dropletId}` - Delete a droplet
- **POST** `/v2/droplets/{dropletId}/actions` - Perform action on droplet
- **GET** `/v2/domains` - List domains
- **POST** `/v2/domains` - Create a domain
- **GET** `/v2/databases` - List databases
- **POST** `/v2/databases` - Create a database cluster
- **GET** `/v2/account` - Get account info
- **GET** `/v2/vpcs` - List All VPCs
- **POST** `/v2/vpcs` - Create a New VPC
- **PUT** `/v2/vpcs/{vpc_id}` - Update a VPC
- **PATCH** `/v2/vpcs/{vpc_id}` - Partially Update a VPC
- **DELETE** `/v2/vpcs/{vpc_id}` - Delete a VPC

## Actions

- list: List droplets (GET /v2/droplets)
- get_by_id: Get a droplet (GET /v2/droplets/{dropletId})
- create: Create a droplet (POST /v2/droplets)
- delete: Delete a droplet (DELETE /v2/droplets/{dropletId})
- create_actions: Perform action on droplet (POST /v2/droplets/{dropletId}/actions)
- list_domains: List domains (GET /v2/domains)
- create_domains: Create a domain (POST /v2/domains)
- list_databases: List databases (GET /v2/databases)
- create_databases: Create a database cluster (POST /v2/databases)
- list_account: Get account info (GET /v2/account)
- list_vpcs: List All VPCs (GET /v2/vpcs)
- create_vpcs: Create a New VPC (POST /v2/vpcs)
- update: Update a VPC (PUT /v2/vpcs/{vpc_id})
- update_vpcs: Partially Update a VPC (PATCH /v2/vpcs/{vpc_id})
- delete_vpcs: Delete a VPC (DELETE /v2/vpcs/{vpc_id})

## Fields

- `name`: string [REQUIRED for create]
- `region`: string [REQUIRED for create] (e.g., "nyc3")
- `size`: string [REQUIRED for create] (e.g., "s-1vcpu-1gb")
- `image`: string [REQUIRED for create] (e.g., "ubuntu-24-04-x64")
- `type`: string [REQUIRED for action] (e.g., "reboot", "power_off", "power_on")

## Example Request Bodies

**Create Droplet:**
```json
{"name": "web-server-01", "region": "nyc3", "size": "s-1vcpu-1gb", "image": "ubuntu-24-04-x64"}
```

**Create Database Cluster:**
```json
{"name": "db-cluster-01", "engine": "pg", "region": "nyc3", "size": "db-s-1vcpu-1gb", "num_nodes": 1}
