---
name: telegram-messaging
description: Send messages and manage Telegram bot interactions. Use when the user
  mentions telegram, message, bot, chat, channel.
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
---

# Telegram-Messaging

Send messages and manage Telegram bot interactions. Use when the user mentions telegram, message, bot, chat, channel.

## API Endpoints

- **POST** `/bot{token}/sendMessage` - Send a message
- **POST** `/bot{token}/getUpdates` - Get updates
- **POST** `/bot{token}/getMe` - Get bot info
- **POST** `/bot{token}/getChat` - Get chat info
- **POST** `/bot{token}/getChatMemberCount` - Get chat member count
- **POST** `/bot{token}/sendPhoto` - Send a photo
- **POST** `/bot{token}/sendDocument` - Send a document
- **POST** `/bot{token}/deleteMessage` - Delete a message
- **POST** `/bot{token}/editMessageText` - Edit a message
- **POST** `/bot{token}/getChatAdministrators` - Get chat admins
- **POST** `/answerCallbackQuery` - Use this method to send answers to callback queries sent from [inline
- **POST** `/answerInlineQuery` - Use this method to send answers to an inline query. On success, *True* is returned.
- **POST** `/answerPreCheckoutQuery` - Once the user has confirmed their payment and shipping details, the Bot API sends the final confirmation in the form of
- **POST** `/answerShippingQuery` - If you sent an invoice requesting a shipping address and the parameter *is\_flexible* was specified, the Bot API will
- **POST** `/addStickerToSet` - Use this method to add a new sticker to a set created by the bot. You **must** use exactly one of the fields

## Actions

- create: Send a message (POST /bot{token}/sendMessage)
- create_getupdates: Get updates (POST /bot{token}/getUpdates)
- create_getme: Get bot info (POST /bot{token}/getMe)
- create_getchat: Get chat info (POST /bot{token}/getChat)
- create_getchatmembercount: Get chat member count (POST /bot{token}/getChatMemberCount)
- create_sendphoto: Send a photo (POST /bot{token}/sendPhoto)
- create_senddocument: Send a document (POST /bot{token}/sendDocument)
- create_deletemessage: Delete a message (POST /bot{token}/deleteMessage)
- create_editmessagetext: Edit a message (POST /bot{token}/editMessageText)
- create_getchatadministrators: Get chat admins (POST /bot{token}/getChatAdministrators)
- query: Use this method to send answers to callback queries sent from [inline (POST /answerCallbackQuery)
- query_answerinlinequery: Use this method to send answers to an inline query. On success, *True* is return (POST /answerInlineQuery)
- query_answerprecheckoutquery: Once the user has confirmed their payment and shipping details, the Bot API send (POST /answerPreCheckoutQuery)
- query_answershippingquery: If you sent an invoice requesting a shipping address and the parameter *is\_flex (POST /answerShippingQuery)
- create_addstickertoset: Use this method to add a new sticker to a set created by the bot. You **must** u (POST /addStickerToSet)

## Fields

- `chat_id`: string or integer [REQUIRED for send]
- `text`: string [REQUIRED for sendMessage]
- `parse_mode`: string [OPTIONAL] (e.g., "HTML", "Markdown")
- `message_id`: integer [REQUIRED for edit/delete]

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
