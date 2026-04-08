---
name: hubspot-crm
description: "Complete HubSpot CRM platform \u2014 contacts, companies, deals, tickets,\
  \ pipelines, associations, properties, owners, engagements, line items, and quotes.\
  \ Use when the user mentions hubspot, contact, company, deal, ticket, pipeline,\
  \ CRM, lead, marketing, association, engagement, owner, quote, line item."
version: 1.0.0
skill_type: external
base_url_env: HUBSPOT_BASE_URL
auth_env_var: HUBSPOT_API_TOKEN
auth_type: bearer
triggers:
  - hubspot
  - contact
  - company
  - deal
  - ticket
  - pipeline
  - CRM
  - lead
license: Apache-2.0
metadata:
  author: lastapi
  version: 2.0.0
compatibility: Requires HUBSPOT_BASE_URL and HUBSPOT_API_TOKEN environment variables.
---

# Hubspot-Crm

Complete HubSpot CRM platform — contacts, companies, deals, tickets, pipelines, associations, properties, owners, engagements, line items, and quotes. Use when the user mentions hubspot, contact, company, deal, ticket, pipeline, CRM, lead, marketing, association, engagement, owner, quote, line item.

## API Endpoints

- **GET** `/crm/v3/objects/contacts` - List contacts
- **POST** `/crm/v3/objects/contacts` - Create a contact
- **GET** `/crm/v3/objects/contacts/{contactId}` - Get a contact by ID
- **PATCH** `/crm/v3/objects/contacts/{contactId}` - Update a contact
- **DELETE** `/crm/v3/objects/contacts/{contactId}` - Archive (delete) a contact
- **POST** `/crm/v3/objects/contacts/search` - Search contacts
- **POST** `/crm/v3/objects/contacts/merge` - Merge two contacts
- **POST** `/crm/v3/objects/contacts/batch/create` - Batch create contacts (up to 100)
- **POST** `/crm/v3/objects/contacts/batch/update` - Batch update contacts (up to 100)
- **POST** `/crm/v3/objects/contacts/batch/read` - Batch read contacts by ID (up to 100)
- **GET** `/crm/v3/objects/companies` - List companies
- **POST** `/crm/v3/objects/companies` - Create a company
- **GET** `/crm/v3/objects/companies/{companyId}` - Get a company by ID
- **PATCH** `/crm/v3/objects/companies/{companyId}` - Update a company
- **DELETE** `/crm/v3/objects/companies/{companyId}` - Archive (delete) a company

## Actions

- list: List contacts (GET /crm/v3/objects/contacts)
- create: Create a contact (POST /crm/v3/objects/contacts)
- get_by_id: Get a contact by ID (GET /crm/v3/objects/contacts/{contactId})
- update: Update a contact (PATCH /crm/v3/objects/contacts/{contactId})
- delete: Archive (delete) a contact (DELETE /crm/v3/objects/contacts/{contactId})
- search: Search contacts (POST /crm/v3/objects/contacts/search)
- create_merge: Merge two contacts (POST /crm/v3/objects/contacts/merge)
- create_batch: Batch create contacts (up to 100) (POST /crm/v3/objects/contacts/batch/create)
- create_update: Batch update contacts (up to 100) (POST /crm/v3/objects/contacts/batch/update)
- create_read: Batch read contacts by ID (up to 100) (POST /crm/v3/objects/contacts/batch/read)
- list_companies: List companies (GET /crm/v3/objects/companies)
- create_companies: Create a company (POST /crm/v3/objects/companies)
- get_by_id_companies: Get a company by ID (GET /crm/v3/objects/companies/{companyId})
- update_companies: Update a company (PATCH /crm/v3/objects/companies/{companyId})
- delete_companies: Archive (delete) a company (DELETE /crm/v3/objects/companies/{companyId})

## Fields

### Contact
- `email`: string [REQUIRED for create] - Contact email address (unique identifier)
- `firstname`: string [OPTIONAL] - First name
- `lastname`: string [OPTIONAL] - Last name
- `phone`: string [OPTIONAL] - Phone number
- `company`: string [OPTIONAL] - Company name (text, not association)
- `jobtitle`: string [OPTIONAL] - Job title
- `lifecyclestage`: string [OPTIONAL] - subscriber, lead, marketingqualifiedlead, salesqualifiedlead, opportunity, customer, evangelist, other
- `hubspot_owner_id`: string [OPTIONAL] - Owner ID (numeric string)
- `hs_lead_status`: string [OPTIONAL] - Lead status (NEW, OPEN, IN_PROGRESS, CONNECTED, etc.)
- `address`: string [OPTIONAL] - Street address
- `city`: string [OPTIONAL] - City
- `state`: string [OPTIONAL] - State/region
- `zip`: string [OPTIONAL] - Postal code
- `country`: string [OPTIONAL] - Country
- `website`: string [OPTIONAL] - Website URL

### Company
- `name`: string [REQUIRED for create] - Company name
- `domain`: string [OPTIONAL] - Company website domain (used for deduplication)
- `industry`: string [OPTIONAL] - Industry (enumeration)
- `phone`: string [OPTIONAL] - Phone number
- `city`: string [OPTIONAL] - City
- `state`: string [OPTIONAL] - State/region
- `country`: string [OPTIONAL] - Country
- `numberofemployees`: string [OPTIONAL] - Number of employees
- `annualrevenue`: string [OPTIONAL] - Annual revenue
- `description`: string [OPTIONAL] - Description
- `hubspot_owner_id`: string [OPTIONAL] - Owner ID
- `lifecyclestage`: string [OPTIONAL] - Lifecycle stage
- `type`: string [OPTIONAL] - Company type (PROSPECT, PARTNER, RESELLER, VENDOR, OTHER)
- `website`: string [OPTIONAL] - Full website URL

### Deal
- `dealname`: string [REQUIRED for create] - Deal name
- `amount`: string [OPTIONAL] - Deal amount (numeric string, e.g., "50000")
- `pipeline`: string [OPTIONAL] - Pipeline ID (default: "default")
- `dealstage`: string [REQUIRED for create] - Stage internal ID (e.g., "appointmentscheduled", "qualifiedtobuy", "closedwon")
- `closedate`: string [OPTIONAL] - Expected close date (ISO 8601 or ms timestamp)
- `hubspot_owner_id`: string [OPTIONAL] - Owner ID
- `dealtype`: string [OPTIONAL] - Deal type (newbusiness, existingbusiness)
- `description`: string [OPTIONAL] - Description
- `hs_priority`: string [OPTIONAL] - Priority (low, medium, high)

### Ticket
- `subject`: string [REQUIRED for create] - Ticket subject
- `content`: string [OPTIONAL] - Ticket description/body
- `hs_pipeline`: string [OPTIONAL] - Pipeline ID (default: "0")
- `hs_pipeline_stage`: string [REQUIRED for create] - Stage ID (e.g., "1" for new, "2" for waiting, "3" for closed)
- `hs_ticket_priority`: string [OPTIONAL] - Priority (LOW, MEDIUM, HIGH)
- `hs_ticket_category`: string [OPTIONAL] - Category
- `hubspot_owner_id`: string [OPTIONAL] - Owner ID
- `source_type`: string [OPTIONAL] - Source (EMAIL, CHAT, PHONE, FORM)

### Engagement / Activity
- `hs_note_body`: string [REQUIRED for notes] - Note body (HTML supported)
- `hs_timestamp`: string [REQUIRED for engagements] - Activity timestamp (ms since epoch)
- `hs_email_subject`: string [OPTIONAL] - Email subject
- `hs_email_text`: string [OPTIONAL] - Email body text
- `hs_email_direction`: string [OPTIONAL] - EMAIL (inbound) or FORWARDED_EMAIL
- `hs_call_body`: string [OPTIONAL] - Call notes
- `hs_call_duration`: string [OPTIONAL] - Call duration in milliseconds
- `hs_call_direction`: string [OPTIONAL] - INBOUND or OUTBOUND
- `hs_call_disposition`: string [OPTIONAL] - Call outcome (connected, no_answer, busy, left_voicemail)
- `hs_task_body`: string [OPTIONAL] - Task description
- `hs_task_subject`: string [REQUIRED for tasks] - Task title
- `hs_task_status`: string [OPTIONAL] - NOT_STARTED, IN_PROGRESS, COMPLETED, DEFERRED
- `hs_task_priority`: string [OPTIONAL] - LOW, MEDIUM, HIGH
- `hs_task_type`: string [OPTIONAL] - TODO, CALL, EMAIL
- `hs_meeting_title`: string [OPTIONAL] - Meeting title
- `hs_meeting_body`: string [OPTIONAL] - Meeting description
- `hs_meeting_start_time`: string [OPTIONAL] - Start time (ms timestamp)
- `hs_meeting_end_time`: string [OPTIONAL] - End time (ms timestamp)
- `hs_meeting_outcome`: string [OPTIONAL] - SCHEDULED, COMPLETED, RESCHEDULED, NO_SHOW, CANCELLED

### Line Item
- `name`: string [REQUIRED for create] - Line item name
- `hs_product_id`: string [OPTIONAL] - Associated product ID
- `quantity`: string [OPTIONAL] - Quantity (default "1")
- `price`: string [REQUIRED for create] - Unit price
- `amount`: string [OPTIONAL] - Total amount (auto-calculated from price * quantity if omitted)
- `discount`: string [OPTIONAL] - Discount percentage
- `hs_recurring_billing_period`: string [OPTIONAL] - Billing period (e.g., "P12M" for 12 months)

### Quote
- `hs_title`: string [REQUIRED for create] - Quote title
- `hs_expiration_date`: string [OPTIONAL] - Expiration date (ms timestamp)
- `hs_status`: string [OPTIONAL] - DRAFT, APPROVAL_NOT_NEEDED, PENDING_APPROVAL, APPROVED, REJECTED
- `hs_sender_firstname`: string [OPTIONAL] - Sender first name
- `hs_sender_lastname`: string [OPTIONAL] - Sender last name
- `hs_sender_email`: string [OPTIONAL] - Sender email
- `hs_sender_company_name`: string [OPTIONAL] - Sender company name
- `hs_comments`: string [OPTIONAL] - Internal comments
- `hs_language`: string [OPTIONAL] - Language code (e.g., "en")

### Search (used with search endpoints)
- `filterGroups`: array [REQUIRED for search] - Array of filter groups (ORed together)
- `filterGroups[].filters`: array [REQUIRED] - Array of filters within a group (ANDed together)
- `filterGroups[].filters[].propertyName`: string [REQUIRED] - Property to filter on
- `filterGroups[].filters[].operator`: string [REQUIRED] - EQ, NEQ, LT, LTE, GT, GTE, BETWEEN, IN, NOT_IN, HAS_PROPERTY, NOT_HAS_PROPERTY, CONTAINS_TOKEN, NOT_CONTAINS_TOKEN
- `filterGroups[].filters[].value`: string [REQUIRED for most operators] - Filter value
- `filterGroups[].filters[].values`: array [REQUIRED for IN, NOT_IN] - Array of values
- `filterGroups[].filters[].highValue`: string [REQUIRED for BETWEEN] - Upper bound
- `sorts`: array [OPTIONAL] - Array of sort objects [{propertyName, direction: "ASCENDING"/"DESCENDING"}]
- `properties`: array [OPTIONAL] - Properties to return
- `limit`: integer [OPTIONAL] - Results per page (max 100, default 10)
- `after`: string [OPTIONAL] - Pagination cursor

### Batch Operations
- `inputs`: array [REQUIRED for batch] - Array of up to 100 record objects
- `inputs[].properties`: object [REQUIRED for batch create/update] - Property key-value pairs
- `inputs[].id`: string [REQUIRED for batch update/read] - Record ID
- `inputs[].idProperty`: string [OPTIONAL for batch read] - Property to use as ID (default: "hs_object_id")

### Association (v4 API)
- `fromObjectType`: string [REQUIRED] - Source object type (contacts, companies, deals, tickets)
- `fromObjectId`: string [REQUIRED] - Source record ID
- `toObjectType`: string [REQUIRED] - Target object type
- `toObjectId`: string [REQUIRED] - Target record ID
- `associationCategory`: string [REQUIRED for create] - HUBSPOT_DEFINED or USER_DEFINED
- `associationTypeId`: integer [REQUIRED for create] - Association type ID (e.g., 1 for contact-to-company)

### Property Definition
- `name`: string [REQUIRED for create] - Internal property name (lowercase, underscores)
- `label`: string [REQUIRED for create] - Display label
- `type`: string [REQUIRED for create] - string, number, date, datetime, enumeration, bool
- `fieldType`: string [REQUIRED for create] - text, textarea, number, date, select, radio, checkbox, booleancheckbox, file
- `groupName`: string [REQUIRED for create] - Property group (e.g., "contactinformation")
- `description`: string [OPTIONAL] - Property description
- `options`: array [OPTIONAL for enumeration] - Array of {label, value, displayOrder} objects
- `hidden`: boolean [OPTIONAL] - Hide from UI (default false)
- `displayOrder`: integer [OPTIONAL] - Display order within group

## Example Requests

**Create Contact:**
```json
{
  "properties": {
    "email": "jane.doe@example.com",
    "firstname": "Jane",
    "lastname": "Doe",
    "phone": "+1-555-0100",
    "company": "Acme Inc",
    "jobtitle": "VP of Engineering",
    "lifecyclestage": "lead"
  }
}
```

**Search Deals by Stage (all deals in "qualifiedtobuy" stage):**
```json
{
  "filterGroups": [
    {
      "filters": [
        {
          "propertyName": "dealstage",
          "operator": "EQ",
          "value": "qualifiedtobuy"
        }
      ]
    }
  ],
  "sorts": [
    {
      "propertyName": "amount",
      "direction": "DESCENDING"
    }
  ],
  "properties": ["dealname", "amount", "dealstage", "closedate", "hubspot_owner_id"],
  "limit": 20
}
```

**Create Association (link contact to company):**
```
PUT /crm/v4/objects/contacts/551/associations/companies/12345
```
```json
[
  {
    "associationCategory": "HUBSPOT_DEFINED",
    "associationTypeId": 1
  }
]
```

**Batch Create Contacts (up to 100):**
```json
{
  "inputs": [
    {
      "properties": {
        "email": "alice@example.com",
        "firstname": "Alice",
        "lastname": "Smith"
      }
    },
    {
      "properties": {
        "email": "bob@example.com",
        "firstname": "Bob",
        "lastname": "Jones"
      }
    },
    {
      "properties": {
        "email": "carol@example.com",
        "firstname": "Carol",
        "lastname": "Williams"
      }
    }
  ]
}
```

**Create a Deal:**
```json
{
  "properties": {
    "dealname": "Enterprise License - Acme Inc",
    "amount": "75000",
    "pipeline": "default",
    "dealstage": "appointmentscheduled",
    "closedate": "2026-06-30T00:00:00.000Z",
    "dealtype": "newbusiness",
    "hubspot_owner_id": "12345678"
  }
}
```

**Create a Ticket:**
```json
{
  "properties": {
    "subject": "Cannot access billing portal",
    "content": "Customer reports 403 error when navigating to billing settings after password reset.",
    "hs_pipeline": "0",
    "hs_pipeline_stage": "1",
    "hs_ticket_priority": "HIGH",
    "source_type": "EMAIL"
  }
}
```

**Search Contacts with Multiple Filters (AND + OR):**
```json
{
  "filterGroups": [
    {
      "filters": [
        {
          "propertyName": "lifecyclestage",
          "operator": "EQ",
          "value": "customer"
        },
        {
          "propertyName": "city",
          "operator": "EQ",
          "value": "San Francisco"
        }
      ]
    },
    {
      "filters": [
        {
          "propertyName": "lifecyclestage",
          "operator": "EQ",
          "value": "customer"
        },
        {
          "propertyName": "city",
          "operator": "EQ",
          "value": "New York"
        }
      ]
    }
  ],
  "properties": ["email", "firstname", "lastname", "city", "company"],
  "limit": 50
}
```

**Create a Custom Property (enumeration type):**
```json
{
  "name": "preferred_contact_method",
  "label": "Preferred Contact Method",
  "type": "enumeration",
  "fieldType": "select",
  "groupName": "contactinformation",
  "description": "How this contact prefers to be reached",
  "options": [
    {"label": "Email", "value": "email", "displayOrder": 1},
    {"label": "Phone", "value": "phone", "displayOrder": 2},
    {"label": "LinkedIn", "value": "linkedin", "displayOrder": 3}
  ]
}
```

**Create a Note and Associate to Contact:**
```json
{
  "properties": {
    "hs_note_body": "<p>Spoke with Jane about renewal. She confirmed budget approval for Q3. Follow up in 2 weeks.</p>",
    "hs_timestamp": "1711929600000",
    "hubspot_owner_id": "12345678"
  },
  "associations": [
    {
      "to": {"id": "551"},
      "types": [
        {
          "associationCategory": "HUBSPOT_DEFINED",
          "associationTypeId": 202
        }
      ]
    }
  ]
}
```

**Create a Line Item:**
```json
{
  "properties": {
    "name": "Annual Pro License",
    "quantity": "5",
    "price": "1200",
    "discount": "10",
    "hs_recurring_billing_period": "P12M"
  }
}
```

**Merge Two Contacts:**
```json
{
  "primaryObjectId": "551",
  "objectIdToMerge": "552"
}
```

**Batch Read Contacts by Email:**
```json
{
  "inputs": [
    {"id": "jane.doe@example.com"},
    {"id": "bob@example.com"}
  ],
  "idProperty": "email",
  "properties": ["email", "firstname", "lastname", "company", "lifecyclestage"]
}
```
