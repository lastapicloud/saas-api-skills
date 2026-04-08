---
name: trello-boards
description: Manage boards, lists, and cards in Trello. Use when the user mentions
  trello, board, card, list, kanban.
version: 1.0.0
skill_type: external
base_url_env: TRELLO_BASE_URL
auth_env_var: TRELLO_API_TOKEN
auth_user_env: TRELLO_API_KEY
auth_type: header
triggers:
  - trello
  - board
  - card
  - list
  - kanban
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires TRELLO_BASE_URL and TRELLO_API_TOKEN environment variables.
---

# Trello-Boards

Manage boards, lists, and cards in Trello. Use when the user mentions trello, board, card, list, kanban.

## API Endpoints

- **GET** `/members/me/boards` - List boards
- **POST** `/cards` - Create a card
- **GET** `/cards/{cardId}` - Get a card
- **PUT** `/cards/{cardId}` - Update a card
- **PUT** `/cards/{cardId}` - Move a card (update idList)
- **GET** `/boards/{boardId}/cards` - List cards on a board
- **POST** `/lists` - Create a list
- **POST** `/cards/{cardId}/actions/comments` - Add a comment to a card
- **POST** `/webhooks` - addWebhooks()
- **GET** `/webhooks/{idWebhook}` - getWebhooksByIdWebhook()
- **PUT** `/webhooks/{idWebhook}` - updateWebhooksByIdWebhook()
- **DELETE** `/webhooks/{idWebhook}` - deleteWebhooksByIdWebhook()
- **POST** `/labels` - addLabels()
- **GET** `/labels/{idLabel}` - getLabelsByIdLabel()
- **PUT** `/labels/{idLabel}` - updateLabelsByIdLabel()

## Actions

- list: List boards (GET /members/me/boards)
- create: Create a card (POST /cards)
- get_by_id: Get a card (GET /cards/{cardId})
- update: Update a card (PUT /cards/{cardId})
- update_cards: Move a card (update idList) (PUT /cards/{cardId})
- list_cards: List cards on a board (GET /boards/{boardId}/cards)
- create_lists: Create a list (POST /lists)
- create_comments: Add a comment to a card (POST /cards/{cardId}/actions/comments)
- create_webhooks: addWebhooks() (POST /webhooks)
- get_by_id_webhooks: getWebhooksByIdWebhook() (GET /webhooks/{idWebhook})
- update_webhooks: updateWebhooksByIdWebhook() (PUT /webhooks/{idWebhook})
- delete: deleteWebhooksByIdWebhook() (DELETE /webhooks/{idWebhook})
- create_labels: addLabels() (POST /labels)
- get_by_id_labels: getLabelsByIdLabel() (GET /labels/{idLabel})
- update_labels: updateLabelsByIdLabel() (PUT /labels/{idLabel})

## Fields

- `boardId`: string [REQUIRED for list_cards] (board ID)
- `cardId`: string [REQUIRED for get_card, update_card, move_card, add_comment] (card ID)
- `idList`: string [REQUIRED for create_card, move_card] (list ID)
- `name`: string [REQUIRED for create_card, create_list] (card or list name)
- `desc`: string [OPTIONAL] (card description)
- `idBoard`: string [REQUIRED for create_list] (board ID for the new list)
- `pos`: string [OPTIONAL] (position: top, bottom, or a positive number)
- `text`: string [REQUIRED for add_comment] (comment text)

## Example Request Bodies

**Create Card:**
```json
{"idList": "list123", "name": "Fix bug #42", "desc": "The login form crashes on submit"}
```

**Move Card:**
```json
{"idList": "list456"}
```

**Add Comment:**
```json
{"text": "This has been resolved in the latest deploy"}
```
