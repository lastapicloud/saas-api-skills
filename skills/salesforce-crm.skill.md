---
name: salesforce-crm
description: "Complete Salesforce CRM platform \u2014 sObjects CRUD, SOQL queries,\
  \ SOSL search, metadata describe, composite operations, limits, approvals, analytics\
  \ reports, and recently viewed records. Use when the user mentions salesforce, CRM,\
  \ lead, opportunity, contact, account, deal, pipeline, case, task, sobject, SOQL,\
  \ SOSL."
version: 1.0.0
skill_type: external
base_url_env: SALESFORCE_BASE_URL
auth_env_var: SALESFORCE_ACCESS_TOKEN
auth_type: bearer
triggers:
  - salesforce
  - CRM
  - lead
  - opportunity
  - contact
  - account
  - deal
  - pipeline
license: Apache-2.0
metadata:
  author: lastapi
  version: 2.0.0
compatibility: Requires SALESFORCE_BASE_URL and SALESFORCE_ACCESS_TOKEN environment
  variables.
---

# Salesforce-Crm

Complete Salesforce CRM platform — sObjects CRUD, SOQL queries, SOSL search, metadata describe, composite operations, limits, approvals, analytics reports, and recently viewed records. Use when the user mentions salesforce, CRM, lead, opportunity, contact, account, deal, pipeline, case, task, sobject, SOQL, SOSL.

## API Endpoints

- **POST** `/sobjects/Account` - Create an Account
- **GET** `/sobjects/Account/{recordId}` - Retrieve an Account by ID
- **PATCH** `/sobjects/Account/{recordId}` - Update an Account
- **DELETE** `/sobjects/Account/{recordId}` - Delete an Account
- **POST** `/sobjects/Contact` - Create a Contact
- **GET** `/sobjects/Contact/{recordId}` - Retrieve a Contact by ID
- **PATCH** `/sobjects/Contact/{recordId}` - Update a Contact
- **DELETE** `/sobjects/Contact/{recordId}` - Delete a Contact
- **POST** `/sobjects/Lead` - Create a Lead
- **GET** `/sobjects/Lead/{recordId}` - Retrieve a Lead by ID
- **PATCH** `/sobjects/Lead/{recordId}` - Update a Lead
- **DELETE** `/sobjects/Lead/{recordId}` - Delete a Lead
- **POST** `/sobjects/Opportunity` - Create an Opportunity
- **GET** `/sobjects/Opportunity/{recordId}` - Retrieve an Opportunity by ID
- **PATCH** `/sobjects/Opportunity/{recordId}` - Update an Opportunity

## Actions

- create: Create an Account (POST /sobjects/Account)
- get_by_id: Retrieve an Account by ID (GET /sobjects/Account/{recordId})
- update: Update an Account (PATCH /sobjects/Account/{recordId})
- delete: Delete an Account (DELETE /sobjects/Account/{recordId})
- create_contact: Create a Contact (POST /sobjects/Contact)
- get_by_id_contact: Retrieve a Contact by ID (GET /sobjects/Contact/{recordId})
- update_contact: Update a Contact (PATCH /sobjects/Contact/{recordId})
- delete_contact: Delete a Contact (DELETE /sobjects/Contact/{recordId})
- create_lead: Create a Lead (POST /sobjects/Lead)
- get_by_id_lead: Retrieve a Lead by ID (GET /sobjects/Lead/{recordId})
- update_lead: Update a Lead (PATCH /sobjects/Lead/{recordId})
- delete_lead: Delete a Lead (DELETE /sobjects/Lead/{recordId})
- create_opportunity: Create an Opportunity (POST /sobjects/Opportunity)
- get_by_id_opportunity: Retrieve an Opportunity by ID (GET /sobjects/Opportunity/{recordId})
- update_opportunity: Update an Opportunity (PATCH /sobjects/Opportunity/{recordId})

## Fields

### Account
- `Name`: string [REQUIRED] - Account name (e.g., "Acme Corporation")
- `Industry`: string [OPTIONAL] - Industry picklist (e.g., "Technology", "Finance", "Healthcare")
- `Type`: string [OPTIONAL] - Account type picklist (e.g., "Prospect", "Customer - Direct", "Partner")
- `Website`: string [OPTIONAL] - Company website URL
- `Phone`: string [OPTIONAL] - Primary phone number
- `BillingStreet`: string [OPTIONAL] - Billing street address
- `BillingCity`: string [OPTIONAL] - Billing city
- `BillingState`: string [OPTIONAL] - Billing state or province
- `BillingPostalCode`: string [OPTIONAL] - Billing postal/ZIP code
- `BillingCountry`: string [OPTIONAL] - Billing country
- `Description`: string [OPTIONAL] - Account description
- `NumberOfEmployees`: integer [OPTIONAL] - Employee count
- `AnnualRevenue`: number [OPTIONAL] - Annual revenue
- `OwnerId`: string [OPTIONAL] - Record owner user ID
- `ParentId`: string [OPTIONAL] - Parent account ID (for account hierarchy)
- `RecordTypeId`: string [OPTIONAL] - Record type ID (when multiple record types exist)

### Contact
- `LastName`: string [REQUIRED] - Contact last name
- `FirstName`: string [OPTIONAL] - Contact first name
- `AccountId`: string [OPTIONAL] - Associated account ID (lookup)
- `Email`: string [OPTIONAL] - Email address
- `Phone`: string [OPTIONAL] - Phone number
- `MobilePhone`: string [OPTIONAL] - Mobile phone number
- `Title`: string [OPTIONAL] - Job title
- `Department`: string [OPTIONAL] - Department
- `MailingStreet`: string [OPTIONAL] - Mailing street address
- `MailingCity`: string [OPTIONAL] - Mailing city
- `MailingState`: string [OPTIONAL] - Mailing state or province
- `MailingPostalCode`: string [OPTIONAL] - Mailing postal/ZIP code
- `MailingCountry`: string [OPTIONAL] - Mailing country
- `Description`: string [OPTIONAL] - Contact description
- `LeadSource`: string [OPTIONAL] - Lead source picklist (e.g., "Web", "Phone Inquiry", "Referral")
- `OwnerId`: string [OPTIONAL] - Record owner user ID
- `RecordTypeId`: string [OPTIONAL] - Record type ID

### Lead
- `LastName`: string [REQUIRED] - Lead last name
- `Company`: string [REQUIRED] - Company name
- `FirstName`: string [OPTIONAL] - Lead first name
- `Email`: string [OPTIONAL] - Email address
- `Phone`: string [OPTIONAL] - Phone number
- `Title`: string [OPTIONAL] - Job title
- `Status`: string [OPTIONAL] - Lead status picklist (e.g., "Open - Not Contacted", "Working - Contacted", "Closed - Converted")
- `LeadSource`: string [OPTIONAL] - Lead source picklist (e.g., "Web", "Phone Inquiry", "Referral")
- `Industry`: string [OPTIONAL] - Industry picklist
- `Rating`: string [OPTIONAL] - Rating picklist (e.g., "Hot", "Warm", "Cold")
- `AnnualRevenue`: number [OPTIONAL] - Estimated annual revenue
- `NumberOfEmployees`: integer [OPTIONAL] - Number of employees
- `Street`: string [OPTIONAL] - Street address
- `City`: string [OPTIONAL] - City
- `State`: string [OPTIONAL] - State or province
- `PostalCode`: string [OPTIONAL] - Postal/ZIP code
- `Country`: string [OPTIONAL] - Country
- `Description`: string [OPTIONAL] - Lead description
- `OwnerId`: string [OPTIONAL] - Record owner user ID
- `RecordTypeId`: string [OPTIONAL] - Record type ID

### Opportunity
- `Name`: string [REQUIRED] - Opportunity name
- `StageName`: string [REQUIRED] - Sales stage picklist (e.g., "Prospecting", "Qualification", "Proposal/Price Quote", "Closed Won", "Closed Lost")
- `CloseDate`: string [REQUIRED] - Expected close date (format: YYYY-MM-DD)
- `AccountId`: string [OPTIONAL] - Associated account ID (lookup)
- `Amount`: number [OPTIONAL] - Opportunity amount
- `Probability`: number [OPTIONAL] - Close probability percentage (0-100)
- `Type`: string [OPTIONAL] - Type picklist (e.g., "New Customer", "Existing Customer - Upgrade")
- `LeadSource`: string [OPTIONAL] - Lead source picklist
- `NextStep`: string [OPTIONAL] - Next step description
- `Description`: string [OPTIONAL] - Opportunity description
- `OwnerId`: string [OPTIONAL] - Record owner user ID
- `RecordTypeId`: string [OPTIONAL] - Record type ID

### Case
- `Subject`: string [OPTIONAL] - Case subject line
- `Description`: string [OPTIONAL] - Detailed case description
- `Status`: string [OPTIONAL] - Status picklist (e.g., "New", "Working", "Escalated", "Closed")
- `Priority`: string [OPTIONAL] - Priority picklist (e.g., "High", "Medium", "Low")
- `Origin`: string [OPTIONAL] - Case origin picklist (e.g., "Email", "Phone", "Web")
- `ContactId`: string [OPTIONAL] - Associated contact ID
- `AccountId`: string [OPTIONAL] - Associated account ID
- `OwnerId`: string [OPTIONAL] - Record owner user ID
- `RecordTypeId`: string [OPTIONAL] - Record type ID

### Task
- `Subject`: string [OPTIONAL] - Task subject
- `Status`: string [OPTIONAL] - Status picklist (e.g., "Not Started", "In Progress", "Completed")
- `Priority`: string [OPTIONAL] - Priority picklist (e.g., "High", "Normal", "Low")
- `ActivityDate`: string [OPTIONAL] - Due date (YYYY-MM-DD)
- `WhoId`: string [OPTIONAL] - Related contact or lead ID
- `WhatId`: string [OPTIONAL] - Related account, opportunity, or other object ID
- `Description`: string [OPTIONAL] - Task description
- `OwnerId`: string [OPTIONAL] - Assigned user ID

### Event
- `Subject`: string [OPTIONAL] - Event subject
- `StartDateTime`: string [OPTIONAL] - Start date/time (ISO 8601: YYYY-MM-DDThh:mm:ss.000Z)
- `EndDateTime`: string [OPTIONAL] - End date/time (ISO 8601: YYYY-MM-DDThh:mm:ss.000Z)
- `WhoId`: string [OPTIONAL] - Related contact or lead ID
- `WhatId`: string [OPTIONAL] - Related account, opportunity, or other object ID
- `Location`: string [OPTIONAL] - Event location
- `Description`: string [OPTIONAL] - Event description
- `IsAllDayEvent`: boolean [OPTIONAL] - All-day event flag
- `OwnerId`: string [OPTIONAL] - Assigned user ID

### SOQL Query
- `q`: string [REQUIRED] - URL-encoded SOQL query string (e.g., `SELECT Id, Name FROM Account WHERE Industry = 'Technology' LIMIT 10`)

### SOSL Search
- `q`: string [REQUIRED] - URL-encoded SOSL search string (e.g., `FIND {Acme} IN ALL FIELDS RETURNING Account(Id, Name), Contact(Id, FirstName, LastName)`)

### Composite Batch
- `batchRequests`: array [REQUIRED] - Array of subrequest objects, each containing `method` (string), `url` (string, relative to base version URL), and optionally `richInput` (object, request body)

### Composite Tree
- `records`: array [REQUIRED] - Array of record objects with a `referenceId` (string, client-side reference) and field values. Child records are nested under the relationship name.

### Approval Request
- `actionType`: string [REQUIRED] - One of "Submit", "Approve", or "Reject"
- `contextId`: string [REQUIRED] - Record ID to submit for approval
- `comments`: string [OPTIONAL] - Approval comment
- `contextActorId`: string [OPTIONAL] - User ID of the submitter
- `nextApproverIds`: array [OPTIONAL] - Array of next approver user IDs

## Example Requests

**Create an Account:**
```json
{
  "Name": "Acme Corporation",
  "Industry": "Technology",
  "Website": "https://acme.example.com",
  "Phone": "+1-555-123-4567",
  "BillingCity": "San Francisco",
  "BillingState": "CA",
  "BillingCountry": "US",
  "NumberOfEmployees": 500,
  "AnnualRevenue": 10000000,
  "Description": "Enterprise software company"
}
```

**Create a Contact linked to an Account:**
```json
{
  "FirstName": "Jane",
  "LastName": "Doe",
  "AccountId": "001xx000003DGbYAAW",
  "Email": "jane.doe@acme.example.com",
  "Phone": "+1-555-987-6543",
  "Title": "VP of Engineering",
  "Department": "Engineering",
  "LeadSource": "Web"
}
```

**Create a Lead:**
```json
{
  "FirstName": "John",
  "LastName": "Smith",
  "Company": "TechStart Inc",
  "Email": "john.smith@techstart.example.com",
  "Phone": "+1-555-222-3333",
  "Title": "CTO",
  "Status": "Open - Not Contacted",
  "LeadSource": "Web",
  "Industry": "Technology",
  "Rating": "Hot"
}
```

**Create an Opportunity:**
```json
{
  "Name": "Acme Corp - Enterprise License",
  "AccountId": "001xx000003DGbYAAW",
  "StageName": "Proposal/Price Quote",
  "CloseDate": "2026-06-30",
  "Amount": 150000,
  "Probability": 60,
  "Type": "New Customer",
  "LeadSource": "Referral",
  "NextStep": "Schedule product demo"
}
```

**SOQL Query — Accounts with related Contacts (relationship query):**
```
GET /query?q=SELECT+Id,Name,Industry,(SELECT+Id,FirstName,LastName,Email+FROM+Contacts)+FROM+Account+WHERE+Industry='Technology'+ORDER+BY+Name+LIMIT+25
```

**SOQL Query — Opportunities closing this quarter:**
```
GET /query?q=SELECT+Id,Name,StageName,Amount,CloseDate,Account.Name+FROM+Opportunity+WHERE+CloseDate=THIS_QUARTER+AND+StageName!='Closed+Lost'+ORDER+BY+Amount+DESC
```

**SOSL Search — Find "Acme" across multiple objects:**
```
GET /search?q=FIND+{Acme}+IN+ALL+FIELDS+RETURNING+Account(Id,Name,Industry),Contact(Id,FirstName,LastName,Email),Opportunity(Id,Name,Amount)
```

**Upsert by External ID (insert or update based on external system ID):**
```
PATCH /sobjects/Account/External_System_Id__c/EXT-12345
```
```json
{
  "Name": "Acme Corporation",
  "Industry": "Technology",
  "Website": "https://acme.example.com"
}
```

**Composite Batch — Multiple operations in one API call:**
```json
{
  "batchRequests": [
    {
      "method": "GET",
      "url": "v59.0/sobjects/Account/001xx000003DGbYAAW"
    },
    {
      "method": "POST",
      "url": "v59.0/sobjects/Contact",
      "richInput": {
        "FirstName": "New",
        "LastName": "Contact",
        "AccountId": "001xx000003DGbYAAW",
        "Email": "new.contact@acme.example.com"
      }
    },
    {
      "method": "PATCH",
      "url": "v59.0/sobjects/Account/001xx000003DGbYAAW",
      "richInput": {
        "Description": "Updated via composite batch"
      }
    }
  ]
}
```

**Composite Tree — Create Account with child Contacts in one call:**
```json
{
  "records": [
    {
      "attributes": {"type": "Account", "referenceId": "ref1"},
      "Name": "New Corp",
      "Industry": "Finance",
      "Contacts": {
        "records": [
          {
            "attributes": {"type": "Contact", "referenceId": "ref2"},
            "FirstName": "Alice",
            "LastName": "Johnson",
            "Email": "alice@newcorp.example.com"
          },
          {
            "attributes": {"type": "Contact", "referenceId": "ref3"},
            "FirstName": "Bob",
            "LastName": "Williams",
            "Email": "bob@newcorp.example.com"
          }
        ]
      }
    }
  ]
}
```

**Submit a record for approval:**
```json
{
  "requests": [
    {
      "actionType": "Submit",
      "contextId": "001xx000003DGbYAAW",
      "comments": "Please approve this account",
      "nextApproverIds": ["005xx000001Svs8AAC"]
    }
  ]
}
```

**Run an analytics report with filters:**
```json
{
  "reportMetadata": {
    "reportFilters": [
      {
        "column": "ACCOUNT.INDUSTRY",
        "operator": "equals",
        "value": "Technology"
      }
    ]
  }
}
```
