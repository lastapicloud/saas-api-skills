---
name: twilio-messaging
description: "Complete Twilio communications platform \u2014 SMS, MMS, voice calls,\
  \ WhatsApp, conversations, phone numbers, verify, usage records, and account management.\
  \ Use when the user mentions twilio, SMS, text, call, phone, WhatsApp, voice, message,\
  \ verify, OTP, number."
version: 1.0.0
skill_type: external
base_url_env: TWILIO_BASE_URL
auth_env_var: TWILIO_AUTH_TOKEN
auth_user_env: TWILIO_ACCOUNT_SID
auth_type: basic
triggers:
  - twilio
  - SMS
  - text
  - call
  - phone
  - WhatsApp
  - voice
  - message
license: Apache-2.0
metadata:
  author: lastapi
  version: 2.0.0
compatibility: Requires TWILIO_BASE_URL and TWILIO_AUTH_TOKEN environment variables.
---

# Twilio-Messaging

Complete Twilio communications platform — SMS, MMS, voice calls, WhatsApp, conversations, phone numbers, verify, usage records, and account management. Use when the user mentions twilio, SMS, text, call, phone, WhatsApp, voice, message, verify, OTP, number.

## API Endpoints

- **POST** `/Accounts/{AccountSid}/Messages.json` - Send an SMS or MMS message
- **GET** `/Accounts/{AccountSid}/Messages.json` - List all messages
- **GET** `/Accounts/{AccountSid}/Messages/{MessageSid}.json` - Get a single message
- **GET** `/Accounts/{AccountSid}/Messages/{MessageSid}/Media.json` - List media attachments on a message
- **GET** `/Accounts/{AccountSid}/Messages/{MessageSid}/Media/{MediaSid}.json` - Get a single media resource
- **DELETE** `/Accounts/{AccountSid}/Messages/{MessageSid}/Media/{MediaSid}.json` - Delete a media resource
- **POST** `/Accounts/{AccountSid}/Calls.json` - Create (initiate) an outbound call
- **GET** `/Accounts/{AccountSid}/Calls.json` - List all calls
- **GET** `/Accounts/{AccountSid}/Calls/{CallSid}.json` - Get a single call
- **POST** `/Accounts/{AccountSid}/Calls/{CallSid}.json` - Modify a live call (redirect, end, etc.)
- **GET** `/Accounts/{AccountSid}/Calls/{CallSid}/Recordings.json` - List recordings for a call
- **GET** `/Accounts/{AccountSid}/Recordings.json` - List all recordings
- **GET** `/Accounts/{AccountSid}/Recordings/{RecordingSid}.json` - Get a single recording
- **DELETE** `/Accounts/{AccountSid}/Recordings/{RecordingSid}.json` - Delete a recording
- **POST** `/Accounts/{AccountSid}/Messages.json` - Send a WhatsApp message (use whatsapp: prefix on To and From)

## Actions

- create: Send an SMS or MMS message (POST /Accounts/{AccountSid}/Messages.json)
- list: List all messages (GET /Accounts/{AccountSid}/Messages.json)
- list_messages: Get a single message (GET /Accounts/{AccountSid}/Messages/{MessageSid}.json)
- list_media_json: List media attachments on a message (GET /Accounts/{AccountSid}/Messages/{MessageSid}/Media.json)
- list_media: Get a single media resource (GET /Accounts/{AccountSid}/Messages/{MessageSid}/Media/{MediaSid}.json)
- delete_media: Delete a media resource (DELETE /Accounts/{AccountSid}/Messages/{MessageSid}/Media/{MediaSid}.json)
- create_calls_json: Create (initiate) an outbound call (POST /Accounts/{AccountSid}/Calls.json)
- list_calls_json: List all calls (GET /Accounts/{AccountSid}/Calls.json)
- list_calls: Get a single call (GET /Accounts/{AccountSid}/Calls/{CallSid}.json)
- create_calls: Modify a live call (redirect, end, etc.) (POST /Accounts/{AccountSid}/Calls/{CallSid}.json)
- list_recordings_json: List recordings for a call (GET /Accounts/{AccountSid}/Calls/{CallSid}/Recordings.json)
- list_recordings_json_2: List all recordings (GET /Accounts/{AccountSid}/Recordings.json)
- list_recordings: Get a single recording (GET /Accounts/{AccountSid}/Recordings/{RecordingSid}.json)
- delete_recordings: Delete a recording (DELETE /Accounts/{AccountSid}/Recordings/{RecordingSid}.json)
- create_messages_json: Send a WhatsApp message (use whatsapp: prefix on To and From) (POST /Accounts/{AccountSid}/Messages.json)

## Fields

### Message (SMS / MMS / WhatsApp)
- `To`: string [REQUIRED] - Destination phone number in E.164 format (e.g., +15551234567). For WhatsApp, use whatsapp:+15551234567
- `From`: string [REQUIRED] - Twilio phone number in E.164 format. For WhatsApp, use whatsapp:+14155238886
- `Body`: string [REQUIRED for SMS] - Message text. Max 1600 characters. Split into 160-char segments for billing (70 for UCS-2 Unicode)
- `MediaUrl`: string [OPTIONAL, MMS only] - URL of media to attach. Supports up to 10 MediaUrl parameters. Accepted types: image/jpeg, image/gif, image/png, audio/*, video/*. Max 5MB per media
- `StatusCallback`: string [OPTIONAL] - URL to receive message status webhooks (queued, sent, delivered, undelivered, failed)
- `MessagingServiceSid`: string [OPTIONAL] - Messaging Service SID (MG...) to use instead of From number. Enables sender pooling and A2P features
- `MaxPrice`: string [OPTIONAL] - Maximum price in USD to pay for the message (e.g., "0.05")
- `ValidityPeriod`: integer [OPTIONAL] - Seconds the message is valid (1-14400, default 14400). Expired undelivered messages fail
- `AccountSid`: string [REQUIRED] - Twilio Account SID from TWILIO_ACCOUNT_SID env var
- `MessageSid`: string [REQUIRED for get/media] - Message SID (SM...)

### Call
- `To`: string [REQUIRED] - Destination phone number in E.164 format
- `From`: string [REQUIRED] - Twilio phone number in E.164 format (must be a voice-capable number)
- `Url`: string [REQUIRED] - TwiML URL providing call instructions. Twilio fetches this URL when the call connects
- `Method`: string [OPTIONAL] - HTTP method to use when fetching Url (GET or POST, default POST)
- `StatusCallback`: string [OPTIONAL] - URL to receive call status webhooks
- `StatusCallbackMethod`: string [OPTIONAL] - HTTP method for StatusCallback (GET or POST, default POST)
- `StatusCallbackEvent`: string [OPTIONAL] - Events to trigger callbacks: initiated, ringing, answered, completed (space-separated)
- `Timeout`: integer [OPTIONAL] - Seconds to wait for answer before timing out (default 60, max 600)
- `Record`: boolean [OPTIONAL] - Whether to record the entire call (true/false, default false)
- `RecordingChannels`: string [OPTIONAL] - mono or dual (default mono)
- `RecordingStatusCallback`: string [OPTIONAL] - URL to receive recording status webhooks
- `MachineDetection`: string [OPTIONAL] - Enable answering machine detection: Enable or DetectMessageEnd
- `Twiml`: string [OPTIONAL] - Inline TwiML content instead of Url (e.g., <Response><Say>Hello</Say></Response>)
- `CallSid`: string [REQUIRED for get/update] - Call SID (CA...)
- `AccountSid`: string [REQUIRED] - Twilio Account SID

### Call Update (Modify Live Call)
- `Url`: string [OPTIONAL] - New TwiML URL to redirect the call to
- `Method`: string [OPTIONAL] - HTTP method for new Url
- `Status`: string [OPTIONAL] - Set to "completed" to end the call, or "canceled" to cancel a queued call
- `Twiml`: string [OPTIONAL] - Inline TwiML to execute immediately

### Phone Number (Purchase / Update)
- `PhoneNumber`: string [REQUIRED for purchase] - The phone number to purchase in E.164 format
- `AreaCode`: string [OPTIONAL for purchase] - Desired area code (alternative to specifying full PhoneNumber)
- `FriendlyName`: string [OPTIONAL] - Human-readable label for the number
- `SmsUrl`: string [OPTIONAL] - URL to handle incoming SMS
- `SmsMethod`: string [OPTIONAL] - HTTP method for SmsUrl (GET or POST)
- `VoiceUrl`: string [OPTIONAL] - URL to handle incoming calls (TwiML)
- `VoiceMethod`: string [OPTIONAL] - HTTP method for VoiceUrl (GET or POST)
- `VoiceFallbackUrl`: string [OPTIONAL] - Fallback URL if VoiceUrl fails
- `StatusCallback`: string [OPTIONAL] - URL for call status webhooks
- `IncomingPhoneNumberSid`: string [REQUIRED for get/update/release] - Phone number SID (PN...)

### Available Number Search
- `CountryCode`: string [REQUIRED] - ISO 3166-1 alpha-2 country code (US, GB, CA, etc.)
- `AreaCode`: string [OPTIONAL] - Filter by area code (US/CA only)
- `Contains`: string [OPTIONAL] - Pattern to match in number (e.g., "555" or "COFFEE" for vanity)
- `SmsEnabled`: boolean [OPTIONAL] - Filter for SMS-capable numbers
- `MmsEnabled`: boolean [OPTIONAL] - Filter for MMS-capable numbers
- `VoiceEnabled`: boolean [OPTIONAL] - Filter for voice-capable numbers
- `InRegion`: string [OPTIONAL] - Filter by region/state (e.g., "NY")
- `InPostalCode`: string [OPTIONAL] - Filter by postal code

### Conversation
- `FriendlyName`: string [OPTIONAL] - Display name for the conversation
- `UniqueName`: string [OPTIONAL] - Unique identifier for the conversation
- `DateCreated`: string [OPTIONAL] - ISO 8601 creation timestamp
- `MessagingServiceSid`: string [OPTIONAL] - Messaging Service SID for the conversation
- `ConversationSid`: string [REQUIRED for get/update/delete/participants/messages] - Conversation SID (CH...)

### Conversation Participant
- `Identity`: string [OPTIONAL] - Unique identity of the participant (for chat users)
- `MessagingBinding.Address`: string [OPTIONAL] - Phone number in E.164 for SMS/WhatsApp participants
- `MessagingBinding.ProxyAddress`: string [OPTIONAL] - Twilio number to use as proxy for the participant

### Conversation Message
- `Author`: string [OPTIONAL] - Identity of the message author
- `Body`: string [REQUIRED] - Message text content

### Verify Service
- `FriendlyName`: string [REQUIRED for create] - Display name for the verification service
- `CodeLength`: integer [OPTIONAL] - Length of the verification code (4-10, default 6)
- `LookupEnabled`: boolean [OPTIONAL] - Enable phone number lookup before sending (default false)
- `SkipSmsToLandlines`: boolean [OPTIONAL] - Skip sending SMS to landlines (default false)
- `DtmfInputRequired`: boolean [OPTIONAL] - Require DTMF input for phone call verifications (default true)
- `ServiceSid`: string [REQUIRED for send/check] - Verify Service SID (VA...)

### Verification (Send)
- `To`: string [REQUIRED] - Phone number or email to verify in E.164 format
- `Channel`: string [REQUIRED] - Delivery channel: sms, call, email, or whatsapp
- `Locale`: string [OPTIONAL] - Locale for the verification message (e.g., "en", "es", "fr")
- `CustomCode`: string [OPTIONAL] - Custom verification code (overrides auto-generated code)
- `Amount`: string [OPTIONAL] - Amount for transaction verification (e.g., "$10.00")
- `Payee`: string [OPTIONAL] - Payee name for transaction verification

### Verification Check
- `To`: string [CONDITIONAL] - Phone number or email that was verified (required if VerificationSid not provided)
- `Code`: string [REQUIRED] - The verification code entered by the user
- `VerificationSid`: string [CONDITIONAL] - Verification SID (VE...) (alternative to To)

### Account
- `FriendlyName`: string [OPTIONAL] - Display name for the account or subaccount
- `Status`: string [OPTIONAL] - Account status: active, suspended, closed

### Usage Records
- `Category`: string [OPTIONAL] - Filter by usage category (e.g., sms, calls, recordings, phonenumbers)
- `StartDate`: string [OPTIONAL] - Start date for usage period (YYYY-MM-DD)
- `EndDate`: string [OPTIONAL] - End date for usage period (YYYY-MM-DD)

## Example Requests

**Send SMS (form-encoded):**
```
To=+15551234567&From=+15559876543&Body=Hello+from+PythonREST!
```

**Send MMS with media (form-encoded):**
```
To=+15551234567&From=+15559876543&Body=Check+out+this+image&MediaUrl=https://example.com/photo.jpg
```

**Send WhatsApp message (form-encoded):**
```
To=whatsapp:+15551234567&From=whatsapp:+14155238886&Body=Your+order+has+shipped!
```

**Make an outbound call (form-encoded):**
```
To=+15551234567&From=+15559876543&Url=http://demo.twilio.com/docs/voice.xml&StatusCallback=https://myapp.com/call-status&Record=true
```

**Make a call with inline TwiML (form-encoded):**
```
To=+15551234567&From=+15559876543&Twiml=<Response><Say+voice="alice">Hello,+this+is+an+automated+call.</Say></Response>
```

**Modify a live call (end it):**
```
Status=completed
```

**Search available US local numbers (query params):**
```
?AreaCode=510&SmsEnabled=true&VoiceEnabled=true&Contains=555
```

**Purchase a phone number (form-encoded):**
```
PhoneNumber=+15105551234&FriendlyName=Main+Office+Line&SmsUrl=https://myapp.com/sms&VoiceUrl=https://myapp.com/voice
```

**Create a Verify service (form-encoded):**
```
FriendlyName=MyApp+Verification&CodeLength=6&LookupEnabled=true
```

**Send a verification code (form-encoded):**
```
To=+15551234567&Channel=sms
```

**Check a verification code (form-encoded):**
```
To=+15551234567&Code=123456
```

**Create a conversation (form-encoded):**
```
FriendlyName=Support+Chat+123&UniqueName=support-chat-123
```

**Add a participant to a conversation (form-encoded):**
```
MessagingBinding.Address=+15551234567&MessagingBinding.ProxyAddress=+15559876543
```

**Create a subaccount (form-encoded):**
```
FriendlyName=Client+ABC+Subaccount
```

**Update a phone number configuration (form-encoded):**
```
FriendlyName=Updated+Label&VoiceUrl=https://myapp.com/new-voice-handler&SmsUrl=https://myapp.com/new-sms-handler
```
