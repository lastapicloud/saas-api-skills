---
name: auth0-management
description: "Complete Auth0 Management API \u2014 users, roles, organizations, connections,\
  \ clients, actions, rules, logs, grants, resource servers, branding, tenants, and\
  \ jobs. Use when the user mentions auth0, user, identity, authentication, role,\
  \ permission, organization, connection, client, action, rule, tenant, branding,\
  \ grant, log, resource server."
version: 1.0.0
skill_type: external
base_url_env: AUTH0_BASE_URL
auth_env_var: AUTH0_MGMT_TOKEN
auth_type: bearer
triggers:
  - auth0
  - user
  - identity
  - authentication
  - role
  - permission
  - organization
  - connection
license: Apache-2.0
metadata:
  author: lastapi
  version: 2.0.0
compatibility: Requires AUTH0_BASE_URL and AUTH0_MGMT_TOKEN environment variables.
---

# Auth0-Management

Complete Auth0 Management API — users, roles, organizations, connections, clients, actions, rules, logs, grants, resource servers, branding, tenants, and jobs. Use when the user mentions auth0, user, identity, authentication, role, permission, organization, connection, client, action, rule, tenant, branding, grant, log, resource server.

## API Endpoints

- **GET** `/users` - List or search users
- **POST** `/users` - Create a user
- **GET** `/users/{user_id}` - Get a user by ID
- **PATCH** `/users/{user_id}` - Update a user
- **DELETE** `/users/{user_id}` - Delete a user
- **GET** `/users/{user_id}/permissions` - List permissions assigned to a user
- **GET** `/users/{user_id}/roles` - List roles assigned to a user
- **POST** `/users/{user_id}/roles` - Assign roles to a user
- **DELETE** `/users/{user_id}/roles` - Remove roles from a user
- **POST** `/users/{user_id}/identities` - Link a user identity (account linking)
- **DELETE** `/users/{user_id}/identities/{provider}/{linked_user_id}` - Unlink a user identity
- **POST** `/users/{user_id}/multifactor/{provider}` - Delete a user's multifactor provider
- **PATCH** `/users/{user_id}` - Block a user (set blocked: true)
- **PATCH** `/users/{user_id}` - Unblock a user (set blocked: false)
- **GET** `/roles` - List all roles

## Actions

- list: List or search users (GET /users)
- create: Create a user (POST /users)
- get_by_id: Get a user by ID (GET /users/{user_id})
- update: Update a user (PATCH /users/{user_id})
- delete: Delete a user (DELETE /users/{user_id})
- list_permissions: List permissions assigned to a user (GET /users/{user_id}/permissions)
- list_roles: List roles assigned to a user (GET /users/{user_id}/roles)
- create_roles: Assign roles to a user (POST /users/{user_id}/roles)
- delete_roles: Remove roles from a user (DELETE /users/{user_id}/roles)
- create_identities: Link a user identity (account linking) (POST /users/{user_id}/identities)
- delete_identities: Unlink a user identity (DELETE /users/{user_id}/identities/{provider}/{linked_user_id})
- add_multifactor: Delete a user's multifactor provider (POST /users/{user_id}/multifactor/{provider})
- update_users: Block a user (set blocked: true) (PATCH /users/{user_id})
- update_users_2: Unblock a user (set blocked: false) (PATCH /users/{user_id})
- list_roles_2: List all roles (GET /roles)

## Fields

### User
- `email`: string [REQUIRED for create] - User's email address (must be unique per connection)
- `password`: string [REQUIRED for create on database connections] - Password (min 8 chars, must meet connection's password policy)
- `connection`: string [REQUIRED for create] - Connection name (e.g., "Username-Password-Authentication", "google-oauth2")
- `user_id`: string [REQUIRED for get, update, delete, role operations] - User ID (e.g., "auth0|64abc123def456"). Must be URL-encoded in paths.
- `name`: string [OPTIONAL] - User's full name
- `given_name`: string [OPTIONAL] - First name
- `family_name`: string [OPTIONAL] - Last name
- `nickname`: string [OPTIONAL] - Nickname (defaults to email prefix if not set)
- `picture`: string [OPTIONAL] - URL to user's profile picture
- `phone_number`: string [OPTIONAL] - Phone number in E.164 format (e.g., "+14155551234")
- `phone_verified`: boolean [OPTIONAL] - Whether phone is verified
- `email_verified`: boolean [OPTIONAL] - Whether email is verified
- `blocked`: boolean [OPTIONAL] - Block or unblock the user
- `user_metadata`: object [OPTIONAL] - User-editable metadata (preferences, profile extras)
- `app_metadata`: object [OPTIONAL] - Admin-only metadata (plans, roles, internal flags)
- `username`: string [OPTIONAL] - Username (only for database connections with username enabled)
- `verify_email`: boolean [OPTIONAL for create] - Send verification email on create (default true)
- `q`: string [OPTIONAL for list] - Lucene query syntax search (e.g., `email:"jane@example.com"`)
- `search_engine`: string [OPTIONAL for list] - Search engine version ("v3" recommended)
- `page`: integer [OPTIONAL for list] - Page number (0-based)
- `per_page`: integer [OPTIONAL for list] - Results per page (max 100, default 50)
- `include_totals`: boolean [OPTIONAL for list] - Include total count in response
- `sort`: string [OPTIONAL for list] - Sort field and order (e.g., "created_at:-1" for desc)
- `fields`: string [OPTIONAL] - Comma-separated list of fields to include or exclude
- `include_fields`: boolean [OPTIONAL] - If true, only return fields listed; if false, exclude them

### Role
- `name`: string [REQUIRED for create] - Role name (must be unique)
- `description`: string [OPTIONAL] - Role description
- `role_id`: string [REQUIRED for get, update, delete] - Role ID (e.g., "rol_abc123def456")

### Role Permissions (for assign/remove)
- `permissions`: array [REQUIRED] - Array of permission objects, each with:
  - `resource_server_identifier`: string [REQUIRED] - API identifier (audience URL)
  - `permission_name`: string [REQUIRED] - Permission name (e.g., "read:users")

### Organization
- `name`: string [REQUIRED for create] - Machine-friendly name (lowercase, no spaces, e.g., "acme-corp")
- `display_name`: string [REQUIRED for create] - Human-friendly display name (e.g., "Acme Corporation")
- `branding`: object [OPTIONAL] - Organization branding: `{ "logo_url": "https://...", "colors": { "primary": "#FF0000", "page_background": "#FFFFFF" } }`
- `metadata`: object [OPTIONAL] - Key-value pairs for org metadata
- `org_id`: string [REQUIRED for get, update, delete] - Organization ID (e.g., "org_abc123def456")
- `enabled_connections`: array [OPTIONAL for create] - Array of `{ "connection_id": "con_...", "assign_membership_on_login": true }`

### Organization Invitation
- `inviter`: object [REQUIRED] - `{ "name": "Admin Name" }`
- `invitee`: object [REQUIRED] - `{ "email": "invitee@example.com" }`
- `client_id`: string [REQUIRED] - Application client ID for the invitation link
- `roles`: array [OPTIONAL] - Role IDs to assign on acceptance
- `send_invitation_email`: boolean [OPTIONAL] - Whether to send the email (default true)
- `ttl_sec`: integer [OPTIONAL] - Invitation TTL in seconds (default 604800 = 7 days)

### Connection
- `name`: string [REQUIRED for create] - Connection name (alphanumeric + hyphens, e.g., "my-database")
- `strategy`: string [REQUIRED for create] - Connection type: "auth0" (database), "google-oauth2", "github", "facebook", "samlp", "waad" (Azure AD), "adfs", "email" (passwordless), "sms" (passwordless)
- `options`: object [OPTIONAL] - Strategy-specific options (password policy, client_id/client_secret for social, etc.)
- `enabled_clients`: array [OPTIONAL] - Client IDs that can use this connection
- `realms`: array [OPTIONAL] - Realms associated with this connection
- `connection_id`: string [REQUIRED for get, update, delete] - Connection ID (e.g., "con_abc123")
- `is_domain_connection`: boolean [OPTIONAL] - Whether this is a domain-level connection

### Client / Application
- `name`: string [REQUIRED for create] - Application name
- `app_type`: string [OPTIONAL] - Application type: "native", "spa", "regular_web", "non_interactive" (M2M)
- `callbacks`: array [OPTIONAL] - Allowed callback URLs
- `allowed_logout_urls`: array [OPTIONAL] - Allowed logout redirect URLs
- `web_origins`: array [OPTIONAL] - Allowed web origins (for CORS)
- `allowed_origins`: array [OPTIONAL] - Allowed origins
- `grant_types`: array [OPTIONAL] - Allowed grant types: "authorization_code", "implicit", "client_credentials", "password", "refresh_token"
- `client_metadata`: object [OPTIONAL] - Custom metadata for the client
- `logo_uri`: string [OPTIONAL] - URL to client logo
- `description`: string [OPTIONAL] - Client description
- `oidc_conformant`: boolean [OPTIONAL] - OIDC conformant mode (default true)
- `token_endpoint_auth_method`: string [OPTIONAL] - "client_secret_post", "client_secret_basic", "none"
- `client_id`: string [REQUIRED for get, update, delete] - Client ID

### Action
- `name`: string [REQUIRED for create] - Action name
- `supported_triggers`: array [REQUIRED for create] - Array of trigger objects: `[{ "id": "post-login", "version": "v3" }]`
- `code`: string [REQUIRED for create] - JavaScript code for the action
- `dependencies`: array [OPTIONAL] - NPM dependencies: `[{ "name": "axios", "version": "1.7.2" }]`
- `secrets`: array [OPTIONAL] - Action secrets: `[{ "name": "MY_SECRET", "value": "secret-value" }]`
- `runtime`: string [OPTIONAL] - Runtime version ("node18" or "node16")
- `action_id`: string [REQUIRED for get, update, delete, deploy, test] - Action ID

### Resource Server / API
- `name`: string [REQUIRED for create] - API name
- `identifier`: string [REQUIRED for create] - API identifier / audience (e.g., "https://api.example.com")
- `scopes`: array [OPTIONAL] - Available permissions: `[{ "value": "read:users", "description": "Read users" }]`
- `signing_alg`: string [OPTIONAL] - Signing algorithm ("RS256" default, "HS256")
- `token_lifetime`: integer [OPTIONAL] - Access token lifetime in seconds (default 86400)
- `token_lifetime_for_web`: integer [OPTIONAL] - Token lifetime for web (default 7200)
- `enforce_policies`: boolean [OPTIONAL] - Enable RBAC (default false)
- `token_dialect`: string [OPTIONAL] - Token dialect: "access_token", "access_token_authz" (includes permissions in token)
- `resource_server_id`: string [REQUIRED for get, update, delete] - Resource server ID

### Branding
- `colors`: object [OPTIONAL] - `{ "primary": "#0059d6", "page_background": "#000000" }`
- `favicon_url`: string [OPTIONAL] - URL to favicon
- `logo_url`: string [OPTIONAL] - URL to logo
- `font`: object [OPTIONAL] - `{ "url": "https://fonts.googleapis.com/css?family=Roboto" }`

### Rule (deprecated)
- `name`: string [REQUIRED for create] - Rule name
- `script`: string [REQUIRED for create] - Rule JavaScript code (receives `function(user, context, callback)`)
- `order`: integer [OPTIONAL] - Execution order (lower = first)
- `enabled`: boolean [OPTIONAL] - Whether the rule is enabled (default true)
- `rule_id`: string [REQUIRED for get, update, delete] - Rule ID

### Job
- `connection_id`: string [REQUIRED for import] - Connection ID to import users into
- `users`: file [REQUIRED for import] - JSON file with user array (multipart/form-data)
- `upsert`: boolean [OPTIONAL for import] - Update existing users (default false)
- `send_completion_email`: boolean [OPTIONAL for import] - Email admin on completion (default true)
- `user_id`: string [REQUIRED for verification email] - User ID to send verification email to
- `client_id`: string [OPTIONAL for verification email] - Client ID for the verification email template

## Example Request Bodies

**Create User (database connection):**
```json
{
  "email": "jane.doe@example.com",
  "password": "SecureP@ssw0rd!",
  "connection": "Username-Password-Authentication",
  "name": "Jane Doe",
  "given_name": "Jane",
  "family_name": "Doe",
  "user_metadata": { "preferred_language": "en" },
  "app_metadata": { "plan": "premium", "signup_source": "marketing" },
  "email_verified": false,
  "verify_email": true
}
```

**Search Users (Lucene query):**
```
GET /users?q=email:"*@example.com" AND app_metadata.plan:"premium"&search_engine=v3&page=0&per_page=25&include_totals=true&sort=created_at:-1
```

**Update User (block):**
```json
PATCH /users/auth0%7C64abc123def456
{
  "blocked": true
}
```

**Assign Roles to User:**
```json
POST /users/auth0%7C64abc123def456/roles
{
  "roles": ["rol_abc123", "rol_def456"]
}
```

**Remove Roles from User:**
```json
DELETE /users/auth0%7C64abc123def456/roles
{
  "roles": ["rol_abc123"]
}
```

**Create Role:**
```json
{
  "name": "Admin",
  "description": "Full administrative access to the management dashboard"
}
```

**Assign Permissions to Role:**
```json
POST /roles/rol_abc123/permissions
{
  "permissions": [
    { "resource_server_identifier": "https://api.example.com", "permission_name": "read:users" },
    { "resource_server_identifier": "https://api.example.com", "permission_name": "write:users" }
  ]
}
```

**Create Organization:**
```json
{
  "name": "acme-corp",
  "display_name": "Acme Corporation",
  "branding": {
    "logo_url": "https://acme.com/logo.png",
    "colors": { "primary": "#3B82F6", "page_background": "#F9FAFB" }
  },
  "metadata": { "industry": "technology", "tier": "enterprise" }
}
```

**Add Members to Organization:**
```json
POST /organizations/org_abc123/members
{
  "members": ["auth0|64abc123def456", "auth0|64xyz789ghi012"]
}
```

**Create Organization Invitation:**
```json
POST /organizations/org_abc123/invitations
{
  "inviter": { "name": "Admin User" },
  "invitee": { "email": "new.member@acme.com" },
  "client_id": "abc123ClientId",
  "roles": ["rol_member"],
  "send_invitation_email": true,
  "ttl_sec": 604800
}
```

**Create Connection (database):**
```json
{
  "name": "my-custom-db",
  "strategy": "auth0",
  "options": {
    "password_policy": "good",
    "brute_force_protection": true
  },
  "enabled_clients": ["abc123ClientId", "def456ClientId"]
}
```

**Create Client (SPA):**
```json
{
  "name": "My SPA Application",
  "app_type": "spa",
  "callbacks": ["https://myapp.com/callback", "http://localhost:3000/callback"],
  "allowed_logout_urls": ["https://myapp.com", "http://localhost:3000"],
  "web_origins": ["https://myapp.com", "http://localhost:3000"],
  "grant_types": ["authorization_code", "implicit", "refresh_token"],
  "oidc_conformant": true
}
```

**Create Action (post-login):**
```json
{
  "name": "Add Custom Claims",
  "supported_triggers": [{ "id": "post-login", "version": "v3" }],
  "code": "exports.onExecutePostLogin = async (event, api) => {\n  const namespace = 'https://myapp.com';\n  api.accessToken.setCustomClaim(`${namespace}/roles`, event.authorization?.roles || []);\n  api.idToken.setCustomClaim(`${namespace}/email`, event.user.email);\n};",
  "dependencies": [],
  "secrets": [{ "name": "NAMESPACE", "value": "https://myapp.com" }],
  "runtime": "node18"
}
```

**Create Resource Server / API:**
```json
{
  "name": "My API",
  "identifier": "https://api.example.com",
  "scopes": [
    { "value": "read:users", "description": "Read user profiles" },
    { "value": "write:users", "description": "Create and update users" },
    { "value": "delete:users", "description": "Delete users" },
    { "value": "read:reports", "description": "Access analytics reports" }
  ],
  "signing_alg": "RS256",
  "token_lifetime": 86400,
  "enforce_policies": true,
  "token_dialect": "access_token_authz"
}
```

**Update Branding:**
```json
PATCH /branding
{
  "colors": { "primary": "#0059D6", "page_background": "#FFFFFF" },
  "logo_url": "https://mycompany.com/logo.png",
  "favicon_url": "https://mycompany.com/favicon.ico",
  "font": { "url": "https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700" }
}
```

**Send Verification Email (Job):**
```json
POST /jobs/verification-email
{
  "user_id": "auth0|64abc123def456",
  "client_id": "abc123ClientId"
}
```

**Link User Identity (Account Linking):**
```json
POST /users/auth0%7C64abc123def456/identities
{
  "provider": "google-oauth2",
  "user_id": "10987654321"
}
```
