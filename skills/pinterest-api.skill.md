---
name: pinterest-api
description: 'Manage pins and boards via Pinterest API. Use when the user mentions
  pinterest, pin, board, social media, image.

  '
version: 1.0.0
skill_type: external
base_url_env: PINTEREST_BASE_URL
auth_env_var: PINTEREST_ACCESS_TOKEN
auth_type: bearer
triggers:
  - pinterest
  - pin
  - board
  - social media
  - image
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires PINTEREST_BASE_URL and PINTEREST_ACCESS_TOKEN environment
  variables.
annotations:
  readOnlyHint: false
  destructiveHint: true
  idempotentHint: false
---

# Pinterest-Api

Manage pins and boards via Pinterest API. Use when the user mentions pinterest, pin, board, social media, image.


## API Endpoints

- **GET** `/pins` - Get a list of the Pins owned by the "operation user_account"
- **POST** `/pins` - Create a Pin on a board or board section owned by the "operation user_account"
- **PATCH** `/pins/{pin_id}` - Update a pin owned by the "operating user_account"
- **DELETE** `/pins/{pin_id}` - Delete a Pins owned by the "operation user_account" - or on a group board that has been shared with this account
- **GET** `/catalogs/product_groups` - Get a list of product groups for a given Catalogs Feed Id owned by the "operation user_account"
- **POST** `/catalogs/products/get_by_product_group_filters` - List products Pins owned by the "operation user_account" that meet the criteria specified in the Catalogs Product Group
- **PATCH** `/catalogs/product_groups/{product_group_id}` - Update product group owned by the "operation user_account" to use in Catalogs
- **DELETE** `/catalogs/product_groups/{product_group_id}` - Delete a product group owned by the "operation user_account" from being in use in Catalogs
- **GET** `/boards` - Get a list of the boards owned by the "operation user_account" + group boards where this account is a collaborator
- **POST** `/boards` - Create a board owned by the "operation user_account"
- **PATCH** `/boards/{board_id}` - Update a board owned by the "operating user_account"
- **DELETE** `/boards/{board_id}` - Delete a board owned by the "operation user_account"
- **GET** `/user_account/websites/verification` - Get verification code for user to install on the website to claim it
- **POST** `/user_account/websites` - Verify a website as a signed-in user
- **DELETE** `/user_account/websites` - Unverifu a website verified by the signed-in user

## Actions

- list: Get a list of the Pins owned by the "operation user_account" (GET /pins)
- create: Create a Pin on a board or board section owned by the "operation user_account" (POST /pins)
- update: Update a pin owned by the "operating user_account" (PATCH /pins/{pin_id})
- delete: Delete a Pins owned by the "operation user_account" - or on a group board that h (DELETE /pins/{pin_id})
- get_list_product_groups: Get a list of product groups for a given Catalogs Feed Id owned by the "operatio (GET /catalogs/product_groups)
- list_products_pins_owned: List products Pins owned by the "operation user_account" that meet the criteria (POST /catalogs/products/get_by_product_group_filters)
- update_product_group_owned: Update product group owned by the "operation user_account" to use in Catalogs (PATCH /catalogs/product_groups/{product_group_id})
- delete_product_group_owned: Delete a product group owned by the "operation user_account" from being in use i (DELETE /catalogs/product_groups/{product_group_id})
- get_list_boards_owned: Get a list of the boards owned by the "operation user_account" + group boards wh (GET /boards)
- create_board_owned_operation: Create a board owned by the "operation user_account" (POST /boards)
- update_board_owned_operating: Update a board owned by the "operating user_account" (PATCH /boards/{board_id})
- delete_board_owned_operation: Delete a board owned by the "operation user_account" (DELETE /boards/{board_id})
- get_verification_code_user: Get verification code for user to install on the website to claim it (GET /user_account/websites/verification)
- create_verify_website_as_signedin: Verify a website as a signed-in user (POST /user_account/websites)
- delete_websites: Unverifu a website verified by the signed-in user (DELETE /user_account/websites)

## Fields

- `board_id`: string [REQUIRED for create] — Board unique identifier
- `media_source`: object [REQUIRED for create] — Media Source configuration
- `title`: string [OPTIONAL] — Title or heading

## Example Request Bodies

**Create Pin:**
```json
{"board_id": "board-12345", "media_source": {"source_type": "image_url", "url": "https://example.com/recipe.jpg"}, "title": "Easy Pasta Recipe"}
```

**Create Board:**
```json
{"name": "Travel Inspiration", "description": "Dream destinations and travel tips"}
```

## Response

**Pin object:**
- `id`: string — Unique pin identifier
- `name`: string — Pin name or title
- `status`: string — Current status
- `created_at`: string — Creation timestamp (ISO 8601)
- `updated_at`: string — Last update timestamp (ISO 8601)

## Error Responses

| Status | Meaning |
|--------|---------|
| 400 | Invalid request body — check required fields and types |
| 401 | Authentication failed — verify API key or token is valid and not expired |
| 403 | Forbidden — insufficient permissions or scope for this action |
| 404 | Resource not found — check the ID or identifier |
| 409 | Conflict — resource already exists or concurrent modification |
| 429 | Rate limited — too many requests, retry after delay |
| 500 | Server error — retry or check service status page |
