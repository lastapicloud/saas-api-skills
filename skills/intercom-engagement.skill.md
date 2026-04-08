---
name: intercom-engagement
description: Manage contacts, conversations, and articles in Intercom. Use when the
  user mentions intercom, contact, conversation, article, help center, customer, support,
  chat.
version: 1.0.0
skill_type: external
base_url_env: INTERCOM_BASE_URL
auth_env_var: INTERCOM_ACCESS_TOKEN
auth_type: bearer
triggers:
  - intercom
  - contact
  - conversation
  - article
  - help center
  - customer
  - support
  - chat
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires INTERCOM_BASE_URL and INTERCOM_ACCESS_TOKEN environment variables.
---

# Intercom-Engagement

Manage contacts, conversations, and articles in Intercom. Use when the user mentions intercom, contact, conversation, article, help center, customer, support, chat.

## API Endpoints

- **GET** `/contacts` - List contacts
- **POST** `/contacts` - Create a contact
- **GET** `/contacts/{contact_id}` - Get a contact
- **GET** `/conversations` - List conversations
- **GET** `/conversations/{conversation_id}` - Get a conversation
- **POST** `/conversations/{conversation_id}/reply` - Reply to a conversation
- **GET** `/articles` - List articles
- **POST** `/articles` - Create an article
- **GET** `/companies` - Retrieve companies
- **POST** `/companies` - Create or Update a company
- **PUT** `/companies/{id}` - Update a company
- **DELETE** `/companies/{id}` - Delete a company
- **PUT** `/articles/{id}` - Update an article
- **DELETE** `/articles/{id}` - Delete an article
- **POST** `/contacts/search` - Search contacts

## Actions

- list: List contacts (GET /contacts)
- create: Create a contact (POST /contacts)
- get_by_id: Get a contact (GET /contacts/{contact_id})
- list_conversations: List conversations (GET /conversations)
- get_by_id_conversations: Get a conversation (GET /conversations/{conversation_id})
- create_reply: Reply to a conversation (POST /conversations/{conversation_id}/reply)
- list_articles: List articles (GET /articles)
- create_articles: Create an article (POST /articles)
- list_companies: Retrieve companies (GET /companies)
- create_companies: Create or Update a company (POST /companies)
- update: Update a company (PUT /companies/{id})
- delete: Delete a company (DELETE /companies/{id})
- update_articles: Update an article (PUT /articles/{id})
- delete_articles: Delete an article (DELETE /articles/{id})
- search: Search contacts (POST /contacts/search)

## Fields

- `contact_id`: string [REQUIRED for get_contact] (contact ID)
- `conversation_id`: string [REQUIRED for get_conversation, reply_to_conversation] (conversation ID)
- `role`: string [REQUIRED for create_contact] (user or lead)
- `email`: string [OPTIONAL for create_contact] (contact email)
- `name`: string [OPTIONAL for create_contact] (contact name)
- `body`: string [REQUIRED for reply_to_conversation] (reply message body)
- `message_type`: string [REQUIRED for reply_to_conversation] (comment or note)
- `admin_id`: string [REQUIRED for reply_to_conversation as admin] (admin ID)
- `title`: string [REQUIRED for create_article] (article title)
- `author_id`: integer [REQUIRED for create_article] (author admin ID)

## Example Request Bodies

**Create Contact:**
```json
{"role": "user", "email": "user@example.com", "name": "Jane Doe"}
```

**Reply to Conversation:**
```json
{"message_type": "comment", "type": "admin", "admin_id": "12345", "body": "Thanks for reaching out!"}
```

**Create Article:**
```json
{"title": "Getting Started", "author_id": 12345, "body": "<p>Welcome to our help center.</p>", "state": "published"}
```
