---
name: guru-knowledge
description: Manage cards and boards via Guru knowledge base. Use when the user mentions
  guru, knowledge base, card, board, wiki, knowledge.
version: 1.0.0
skill_type: external
base_url_env: GURU_BASE_URL
auth_env_var: GURU_API_TOKEN
auth_user_env: GURU_USER_EMAIL
auth_type: basic
triggers:
  - guru
  - knowledge base
  - card
  - board
  - wiki
  - knowledge
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires GURU_BASE_URL and GURU_API_TOKEN environment variables.
---

# Guru-Knowledge

Manage cards and boards via Guru knowledge base. Use when the user mentions guru, knowledge base, card, board, wiki, knowledge.

## API Endpoints

- **GET** `/api/v1/cards` - List cards
- **POST** `/api/v1/cards` - Create card
- **GET** `/api/v1/cards/{id}` - Get card
- **PUT** `/api/v1/cards/{id}` - Update card
- **DELETE** `/api/v1/cards/{id}` - Delete card
- **GET** `/api/v1/boards` - List boards
- **POST** `/api/v1/search/cardmgr` - Search cards
- **GET** `/api/v1/collections` - List collections
- **POST** `/insights/search` - <p> Returns a list of insights in your Amazon Web Services account. You can specify which insights are returned by
- **POST** `/insights` - Returns a list of insights in your Amazon Web Services account. You can specify which insights are returned by their
- **GET** `/insights/{Id}` - Returns details about an insight that you specify using its ID.
- **DELETE** `/insights/{Id}` - Deletes the insight along with the associated anomalies, events and recommendations.
- **POST** `/channels` - Returns a list of notification channels configured for DevOps Guru. Each notification channel is used to notify you
- **DELETE** `/channels/{Id}` - Removes a notification channel from DevOps Guru. A notification channel is used to notify you when DevOps Guru
- **PUT** `/channels` - <p> Adds a notification channel to DevOps Guru. A notification channel is used to notify you about important DevOps

## Actions

- list: List cards (GET /api/v1/cards)
- create: Create card (POST /api/v1/cards)
- get_by_id: Get card (GET /api/v1/cards/{id})
- update: Update card (PUT /api/v1/cards/{id})
- delete: Delete card (DELETE /api/v1/cards/{id})
- list_boards: List boards (GET /api/v1/boards)
- create_cardmgr: Search cards (POST /api/v1/search/cardmgr)
- list_collections: List collections (GET /api/v1/collections)
- search: <p> Returns a list of insights in your Amazon Web Services account. You can spec (POST /insights/search)
- create_insights: Returns a list of insights in your Amazon Web Services account. You can specify (POST /insights)
- get_by_id_insights: Returns details about an insight that you specify using its ID. (GET /insights/{Id})
- delete_insights: Deletes the insight along with the associated anomalies, events and recommendati (DELETE /insights/{Id})
- create_channels: Returns a list of notification channels configured for DevOps Guru. Each notific (POST /channels)
- delete_channels: Removes a notification channel from DevOps Guru. A notification channel is used (DELETE /channels/{Id})
- update_channels: <p> Adds a notification channel to DevOps Guru. A notification channel is used t (PUT /channels)

## Fields

- `preferredPhrase`: string [REQUIRED for create]
- `content`: string [REQUIRED for create]
- `collection`: object [OPTIONAL]

## Example Request Bodies

**Create Card:**
```json
{"preferredPhrase": "Onboarding Guide", "content": "<p>Welcome to the team! Here is everything you need to get started.</p>", "collection": {"id": "col-abc123"}}
```

**Search Cards:**
```json
{"searchTerms": "deployment process", "collectionIds": ["col-abc123"]}
```
