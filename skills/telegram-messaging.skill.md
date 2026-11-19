---
name: telegram-messaging
description: "Send messages and manage Telegram bot interactions. Use when the user\
  \ mentions telegram, message, bot, chat, channel.\n (API 5.0.0)"
version: 1.0.0
skill_type: external
base_url_env: TELEGRAM_BASE_URL
auth_env_var: TELEGRAM_BOT_TOKEN
auth_type: header
triggers:
  - telegram
  - message
  - bot
  - chat
  - channel
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires TELEGRAM_BASE_URL and TELEGRAM_BOT_TOKEN environment variables.
annotations:
  readOnlyHint: false
  destructiveHint: false
  idempotentHint: false
---

# Telegram-Messaging

Send messages and manage Telegram bot interactions. Use when the user mentions telegram, message, bot, chat, channel.
 (API 5.0.0)

## API Endpoints

- **POST** `/answerCallbackQuery` - Use this method to send answers to callback queries sent from [inline
- **POST** `/answerInlineQuery` - Use this method to send answers to an inline query. On success, *True* is returned.
- **POST** `/answerPreCheckoutQuery` - Once the user has confirmed their payment and shipping details, the Bot API sends the final confirmation in the form of
- **POST** `/answerShippingQuery` - If you sent an invoice requesting a shipping address and the parameter *is\_flexible* was specified, the Bot API will
- **POST** `/addStickerToSet` - Use this method to add a new sticker to a set created by the bot. You **must** use exactly one of the fields
- **POST** `/close` - Use this method to close the bot instance before moving it from one local server to another. You need to delete the
- **POST** `/copyMessage` - Use this method to copy messages of any kind. The method is analogous to the method
- **POST** `/createNewStickerSet` - Use this method to create a new sticker set owned by a user. The bot will be able to edit the sticker set thus created.
- **POST** `/deleteChatPhoto` - Use this method to delete a chat photo. Photos can't be changed for private chats. The bot must be an administrator in
- **POST** `/deleteChatStickerSet` - Use this method to delete a group sticker set from a supergroup. The bot must be an administrator in the chat for this
- **POST** `/deleteMessage` - Use this method to delete a message, including service messages, with the following limitations:
- **POST** `/deleteStickerFromSet` - Use this method to delete a sticker from a set created by the bot. Returns *True* on success.
- **POST** `/deleteWebhook` - Use this method to remove webhook integration if you decide to switch back to
- **POST** `/editMessageCaption` - Use this method to edit captions of messages. On success, if the edited message is not an inline message, the edited
- **POST** `/editMessageLiveLocation` - Use this method to edit live location messages. A location can be edited until its *live\_period* expires or editing is

## Actions

- query: Use this method to send answers to callback queries sent from [inline (POST /answerCallbackQuery)
- create_use_this_method_send: Use this method to send answers to an inline query. On success, *True* is return (POST /answerInlineQuery)
- create_once_user_has_confirmed: Once the user has confirmed their payment and shipping details, the Bot API send (POST /answerPreCheckoutQuery)
- create_if_you_sent_invoice: If you sent an invoice requesting a shipping address and the parameter *is\_flex (POST /answerShippingQuery)
- create: Use this method to add a new sticker to a set created by the bot. You **must** u (POST /addStickerToSet)
- create_use_this_method_close: Use this method to close the bot instance before moving it from one local server (POST /close)
- create_use_this_method_copy: Use this method to copy messages of any kind. The method is analogous to the met (POST /copyMessage)
- create_use_this_method_create: Use this method to create a new sticker set owned by a user. The bot will be abl (POST /createNewStickerSet)
- create_use_this_method_delete: Use this method to delete a chat photo. Photos can't be changed for private chat (POST /deleteChatPhoto)
- create_deletechatstickerset: Use this method to delete a group sticker set from a supergroup. The bot must be (POST /deleteChatStickerSet)
- create_deletemessage: Use this method to delete a message, including service messages, with the follow (POST /deleteMessage)
- create_deletestickerfromset: Use this method to delete a sticker from a set created by the bot. Returns *True (POST /deleteStickerFromSet)
- create_use_this_method_remove: Use this method to remove webhook integration if you decide to switch back to (POST /deleteWebhook)
- create_use_this_method_edit: Use this method to edit captions of messages. On success, if the edited message (POST /editMessageCaption)
- create_editmessagelivelocation: Use this method to edit live location messages. A location can be edited until i (POST /editMessageLiveLocation)

## Fields

- `chat_id`: string or integer [REQUIRED for send] — Chat unique identifier
- `text`: string [REQUIRED for sendMessage] — Text content
- `parse_mode`: string [OPTIONAL] (e.g., "HTML", "Markdown") — Parse Mode
- `message_id`: integer [REQUIRED for edit/delete] — Message unique identifier

## Example Request Bodies

**Send a Message:**
```json
{
  "chat_id": "123456789",
  "text": "Hello from the bot!",
  "parse_mode": "HTML"
}
```

**Edit a Message:**
```json
{
  "chat_id": "123456789",
  "message_id": 42,
  "text": "Updated message content"
}
```

## Response

**Answercallbackquery object:**
- `id`: string — Unique answercallbackquery identifier
- `name`: string — Answercallbackquery name or title
- `status`: string — Current status
- `type`: string — Answercallbackquery type or category
- `created_at`: string — Creation timestamp (ISO 8601)
- `updated_at`: string — Last update timestamp (ISO 8601)

## Error Responses

| Status | Meaning |
|--------|---------|
| 400 | Invalid request body — check required fields and types |
| 401 | Authentication failed — verify API key or token is valid and not expired |
| 403 | Forbidden — insufficient permissions or scope for this action |
| 409 | Conflict — resource already exists or concurrent modification |
| 429 | Rate limited — too many requests, retry after delay |
| 500 | Server error — retry or check service status page |
