---
name: resend-email
description: Send transactional emails and manage domains via the Resend API. Use
  when the user mentions resend, email, send email, transactional.
version: 1.0.0
skill_type: external
base_url_env: RESEND_BASE_URL
auth_env_var: RESEND_API_KEY
auth_type: bearer
triggers:
  - resend
  - email
  - send email
  - transactional
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires RESEND_BASE_URL and RESEND_API_KEY environment variables.
---

# Resend-Email

Send transactional emails and manage domains via the Resend API. Use when the user mentions resend, email, send email, transactional.

## API Endpoints

- **POST** `/emails` - Send an email
- **GET** `/emails/{email_id}` - Get email details
- **GET** `/emails` - List emails
- **GET** `/domains` - List domains
- **POST** `/domains` - Create a domain
- **GET** `/contacts` - Retrieve a list of contacts
- **POST** `/contacts` - Create a new contact
- **PATCH** `/contacts/{id}` - Update a single contact by ID or email
- **DELETE** `/contacts/{id}` - Remove an existing contact by ID or email
- **GET** `/topics` - Retrieve a list of topics
- **POST** `/topics` - Create a new topic
- **PATCH** `/topics/{id}` - Update an existing topic
- **DELETE** `/topics/{id}` - Remove an existing topic
- **PATCH** `/domains/{domain_id}` - Update an existing domain
- **DELETE** `/domains/{domain_id}` - Remove an existing domain

## Actions

- create: Send an email (POST /emails)
- get_by_id: Get email details (GET /emails/{email_id})
- list: List emails (GET /emails)
- list_domains: List domains (GET /domains)
- create_domains: Create a domain (POST /domains)
- list_contacts: Retrieve a list of contacts (GET /contacts)
- create_contacts: Create a new contact (POST /contacts)
- update: Update a single contact by ID or email (PATCH /contacts/{id})
- delete: Remove an existing contact by ID or email (DELETE /contacts/{id})
- list_topics: Retrieve a list of topics (GET /topics)
- create_topics: Create a new topic (POST /topics)
- update_topics: Update an existing topic (PATCH /topics/{id})
- delete_topics: Remove an existing topic (DELETE /topics/{id})
- update_domains: Update an existing domain (PATCH /domains/{domain_id})
- delete_domains: Remove an existing domain (DELETE /domains/{domain_id})

## Fields

- `from`: string [REQUIRED for send_email] (sender email address)
- `to`: string or array [REQUIRED for send_email] (recipient email addresses)
- `subject`: string [REQUIRED for send_email] (email subject)
- `html`: string [OPTIONAL for send_email] (HTML body content)
- `text`: string [OPTIONAL for send_email] (plain text body content)
- `email_id`: string [REQUIRED for get_email] (email ID)
- `name`: string [REQUIRED for create_domain] (domain name)

## Example Request Bodies

**Send Email:**
```json
{"from": "noreply@example.com", "to": ["user@example.com"], "subject": "Hello", "html": "<p>Hello from PythonREST!</p>"}
```

**Create Domain:**
```json
{"name": "example.com"}
```
