---
name: insightly-crm
description: Manage contacts, organizations, opportunities, and projects in Insightly
  CRM. Use when the user mentions insightly, insightly crm, insightly contact, insightly
  opportunity, insightly project.
version: 1.0.0
skill_type: external
base_url_env: INSIGHTLY_BASE_URL
auth_env_var: INSIGHTLY_API_KEY
auth_type: basic
triggers:
  - insightly
  - insightly crm
  - insightly contact
  - insightly opportunity
  - insightly project
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires INSIGHTLY_BASE_URL and INSIGHTLY_API_KEY environment variables.
---

# Insightly-Crm

Manage contacts, organizations, opportunities, and projects in Insightly CRM. Use when the user mentions insightly, insightly crm, insightly contact, insightly opportunity, insightly project.

## API Endpoints

- **GET** `/v3.1/Contacts` - List contacts
- **POST** `/v3.1/Contacts` - Create a contact
- **GET** `/v3.1/Contacts/{id}` - Get a contact by ID
- **PUT** `/v3.1/Contacts/{id}` - Update a contact
- **DELETE** `/v3.1/Contacts/{id}` - Delete a contact
- **GET** `/v3.1/Organisations` - List organizations
- **POST** `/v3.1/Organisations` - Create an organization
- **GET** `/v3.1/Opportunities` - List opportunities
- **POST** `/v3.1/Opportunities` - Create an opportunity
- **GET** `/v3.1/Projects` - List projects
- **GET** `/ActivitySets`
- **GET** `/ActivitySets/{id}`
- **GET** `/Comments/{id}/FileAttachments`
- **POST** `/Comments/{id}/FileAttachments`
- **PUT** `/Comments`

## Actions

- list: List contacts (GET /v3.1/Contacts)
- create: Create a contact (POST /v3.1/Contacts)
- get_by_id: Get a contact by ID (GET /v3.1/Contacts/{id})
- update: Update a contact (PUT /v3.1/Contacts/{id})
- delete: Delete a contact (DELETE /v3.1/Contacts/{id})
- list_organisations: List organizations (GET /v3.1/Organisations)
- create_organisations: Create an organization (POST /v3.1/Organisations)
- list_opportunities: List opportunities (GET /v3.1/Opportunities)
- create_opportunities: Create an opportunity (POST /v3.1/Opportunities)
- list_projects: List projects (GET /v3.1/Projects)
- list_activitysets: GET /ActivitySets (GET /ActivitySets)
- get_by_id_activitysets: GET /ActivitySets/{id} (GET /ActivitySets/{id})
- list_fileattachments: GET /Comments/{id}/FileAttachments (GET /Comments/{id}/FileAttachments)
- create_fileattachments: POST /Comments/{id}/FileAttachments (POST /Comments/{id}/FileAttachments)
- update_comments: PUT /Comments (PUT /Comments)

## Fields

- `id`: integer [REQUIRED for get_contact, update_contact, delete_contact] (record ID)
- `FIRST_NAME`: string [OPTIONAL] (first name)
- `LAST_NAME`: string [OPTIONAL] (last name)
- `EMAIL_ADDRESS`: string [OPTIONAL] (email address)
- `PHONE`: string [OPTIONAL] (phone number)
- `ORGANISATION_NAME`: string [REQUIRED for create_organization] (organization name)
- `OPPORTUNITY_NAME`: string [REQUIRED for create_opportunity] (opportunity name)
- `OPPORTUNITY_STATE`: string [OPTIONAL] (Open, Won, Lost, Abandoned, Suspended)
- `BID_AMOUNT`: number [OPTIONAL] (opportunity value)
- `PROJECT_NAME`: string [OPTIONAL] (project name)

## Example Request Bodies

**Create Contact:**
```json
{"FIRST_NAME": "Jane", "LAST_NAME": "Doe", "EMAIL_ADDRESS": "jane@example.com"}
```

**Create Opportunity:**
```json
{"OPPORTUNITY_NAME": "Enterprise License", "OPPORTUNITY_STATE": "Open", "BID_AMOUNT": 50000}
```
