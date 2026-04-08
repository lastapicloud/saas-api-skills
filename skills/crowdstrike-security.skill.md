---
name: crowdstrike-security
description: Manage detections, hosts, and incidents via CrowdStrike Falcon. Use when
  the user mentions crowdstrike, falcon, edr, detection, host, incident, threat.
version: 1.0.0
skill_type: external
base_url_env: CROWDSTRIKE_BASE_URL
auth_env_var: CROWDSTRIKE_API_TOKEN
auth_type: bearer
triggers:
  - crowdstrike
  - falcon
  - edr
  - detection
  - host
  - incident
  - threat
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires CROWDSTRIKE_BASE_URL and CROWDSTRIKE_API_TOKEN environment
  variables.
---

# Crowdstrike-Security

Manage detections, hosts, and incidents via CrowdStrike Falcon. Use when the user mentions crowdstrike, falcon, edr, detection, host, incident, threat.

## API Endpoints

- **GET** `/detects/queries/detects/v1` - List detection IDs
- **POST** `/detects/entities/summaries/GET/v1` - Get detection details
- **PATCH** `/detects/entities/detects/v2` - Update detection status
- **GET** `/devices/queries/devices/v1` - List host IDs
- **POST** `/devices/entities/devices/v2` - Get host details
- **GET** `/incidents/queries/incidents/v1` - List incident IDs
- **POST** `/incidents/entities/incidents/GET/v1` - Get incident details
- **POST** `/real-time-response/entities/sessions/v1` - Start RTR session

## Actions

- list: List detection IDs (GET /detects/queries/detects/v1)
- create: Get detection details (POST /detects/entities/summaries/GET/v1)
- patch_v2: Update detection status (PATCH /detects/entities/detects/v2)
- list_v1: List host IDs (GET /devices/queries/devices/v1)
- create_v2: Get host details (POST /devices/entities/devices/v2)
- list_v1_2: List incident IDs (GET /incidents/queries/incidents/v1)
- create_v1: Get incident details (POST /incidents/entities/incidents/GET/v1)
- create_v1_2: Start RTR session (POST /real-time-response/entities/sessions/v1)

## Fields

- `ids`: array [REQUIRED for get operations]
- `filter`: string [OPTIONAL] (FQL filter)
- `status`: string [OPTIONAL for update]

## Example Request Bodies

**Get Detection Details:**
```json
{"ids": ["ldt:abc123:456", "ldt:def789:012"]}
```

**Update Detection Status:**
```json
{"ids": ["ldt:abc123:456"], "status": "closed"}
