---
name: clerk-auth
description: Manage users and organizations via the Clerk Backend API. Use when the
  user mentions clerk, user, organization, session, invite.
version: 1.0.0
skill_type: external
base_url_env: CLERK_BASE_URL
auth_env_var: CLERK_SECRET_KEY
auth_type: bearer
triggers:
  - clerk
  - user
  - organization
  - session
  - invite
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires CLERK_BASE_URL and CLERK_SECRET_KEY environment variables.
---

# Clerk-Auth

Manage users and organizations via the Clerk Backend API. Use when the user mentions clerk, user, organization, session, invite.

## API Endpoints

- **GET** `/users` - List users
- **POST** `/users` - Create a user
- **GET** `/users/{user_id}` - Get user details
- **PATCH** `/users/{user_id}` - Update a user
- **DELETE** `/users/{user_id}` - Delete a user
- **GET** `/organizations` - List organizations
- **GET** `/jwt_templates` - List all templates
- **POST** `/jwt_templates` - Create a JWT template
- **PATCH** `/jwt_templates/{template_id}` - Update a JWT template
- **DELETE** `/jwt_templates/{template_id}` - Delete a Template
- **GET** `/saml_connections` - Get a list of SAML Connections for an instance
- **POST** `/saml_connections` - Create a SAML Connection
- **PATCH** `/saml_connections/{saml_connection_id}` - Update a SAML Connection
- **DELETE** `/saml_connections/{saml_connection_id}` - Delete a SAML Connection
- **GET** `/oauth_applications` - Get a list of OAuth applications for an instance

## Actions

- list: List users (GET /users)
- create: Create a user (POST /users)
- get_by_id: Get user details (GET /users/{user_id})
- update: Update a user (PATCH /users/{user_id})
- delete: Delete a user (DELETE /users/{user_id})
- list_organizations: List organizations (GET /organizations)
- list_jwt_templates: List all templates (GET /jwt_templates)
- create_jwt_templates: Create a JWT template (POST /jwt_templates)
- update_jwt_templates: Update a JWT template (PATCH /jwt_templates/{template_id})
- delete_jwt_templates: Delete a Template (DELETE /jwt_templates/{template_id})
- list_saml_connections: Get a list of SAML Connections for an instance (GET /saml_connections)
- create_saml_connections: Create a SAML Connection (POST /saml_connections)
- update_saml_connections: Update a SAML Connection (PATCH /saml_connections/{saml_connection_id})
- delete_saml_connections: Delete a SAML Connection (DELETE /saml_connections/{saml_connection_id})
- list_oauth_applications: Get a list of OAuth applications for an instance (GET /oauth_applications)

## Fields

- `user_id`: string [REQUIRED for get_user, update_user, delete_user] (user ID)
- `email_address`: array [REQUIRED for create_user] (list of email addresses)
- `password`: string [OPTIONAL for create_user] (user password)
- `first_name`: string [OPTIONAL] (user first name)
- `last_name`: string [OPTIONAL] (user last name)
- `username`: string [OPTIONAL] (username)
- `limit`: integer [OPTIONAL for list_users, list_organizations] (max results)
- `offset`: integer [OPTIONAL for list_users, list_organizations] (pagination offset)

## Example Request Bodies

**Create User:**
```json
{"email_address": ["user@example.com"], "password": "SecureP@ss123!", "first_name": "Test", "last_name": "User"}
```

**Update User:**
```json
{"first_name": "Updated", "last_name": "Name"}
```
