---
name: capsule-crm
description: Manage contacts, opportunities, and cases via Capsule CRM. Use when the
  user mentions capsule, crm, contact, opportunity, case, party.
version: 1.0.0
skill_type: external
base_url_env: CAPSULE_BASE_URL
auth_env_var: CAPSULE_API_TOKEN
auth_type: bearer
triggers:
  - capsule
  - crm
  - contact
  - opportunity
  - case
  - party
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires CAPSULE_BASE_URL and CAPSULE_API_TOKEN environment variables.
---

# Capsule-Crm

Manage contacts, opportunities, and cases via Capsule CRM. Use when the user mentions capsule, crm, contact, opportunity, case, party.

## API Endpoints

- **GET** `/api/v2/parties` - List parties
- **POST** `/api/v2/parties` - Create a party
- **GET** `/api/v2/parties/{partyId}` - Get party by ID
- **PUT** `/api/v2/parties/{partyId}` - Update a party
- **DELETE** `/api/v2/parties/{partyId}` - Delete a party
- **GET** `/api/v2/opportunities` - List opportunities
- **POST** `/api/v2/opportunities` - Create an opportunity
- **GET** `/api/v2/cases` - List cases

## Actions

- list: List parties (GET /api/v2/parties)
- create: Create a party (POST /api/v2/parties)
- get_by_id: Get party by ID (GET /api/v2/parties/{partyId})
- update: Update a party (PUT /api/v2/parties/{partyId})
- delete: Delete a party (DELETE /api/v2/parties/{partyId})
- list_opportunities: List opportunities (GET /api/v2/opportunities)
- create_opportunities: Create an opportunity (POST /api/v2/opportunities)
- list_cases: List cases (GET /api/v2/cases)

## Fields

- `type`: string [REQUIRED for create] (person or organisation)
- `firstName`: string [OPTIONAL]
- `lastName`: string [OPTIONAL]

## Example Request Bodies

**Create Party:**
```json
{"type": "person", "firstName": "John", "lastName": "Doe"}
```

**Create Opportunity:**
```json
{"name": "Enterprise Deal", "value": 50000, "milestone": "Proposal"}
