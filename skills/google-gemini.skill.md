---
name: google-gemini
description: Google Gemini AI models. Use when the user mentions gemini, google AI, google AI studio, multimodal AI, Gemini Advanced.
version: 1.0.0
skill_type: external
base_url_env: GOOGLE_GEMINI_BASE_URL
auth_env_var: GOOGLE_GEMINI_API_KEY
auth_type: bearer
triggers:
  - gemini
  - google AI
  - google AI studio
  - multimodal AI
  - Gemini Advanced
license: Proprietary
metadata:
  author: lastapi
  version: 1.0.0
  documentation: https://ai.google.dev/gemini-api/docs
---

# Google-Gemini

Google Gemini AI models. Use when the user mentions gemini, google AI, google AI studio, multimodal AI, Gemini Advanced.

## API Endpoints

- **POST** `/v1beta/models/{model}:generateContent` - Generate content
- **POST** `/v1beta/models/{model}:streamGenerateContent` - Stream generate content
- **GET** `/v1beta/models` - List available models
- **GET** `/v1beta/models/{model}` - Get model information
- **POST** `/v1beta/models/{model}:countTokens` - Count tokens
- **POST** `/v1beta/models/{model}:embedContent` - Generate embeddings
- **POST** `/v1beta/models/{model}:batchEmbedContents` - Batch embeddings

## Actions

- generate_content: Generate content (POST /v1beta/models/{model}:generateContent)
- stream_generate: Stream generate content (POST /v1beta/models/{model}:streamGenerateContent)
- list_models: List available models (GET /v1beta/models)
- get_model: Get model information (GET /v1beta/models/{model})
- count_tokens: Count tokens (POST /v1beta/models/{model}:countTokens)
- embed_content: Generate embeddings (POST /v1beta/models/{model}:embedContent)
- batch_embed: Batch embeddings (POST /v1beta/models/{model}:batchEmbedContents)

## Fields

- `model`: string [REQUIRED] - Model name (e.g., gemini-2.0-flash, gemini-pro)
- `contents`: array [REQUIRED] - Content parts (text, images, video)
- `generationConfig`: object [OPTIONAL] - Generation config
- `systemInstruction`: string [OPTIONAL] - System instruction
- `temperature`: number [OPTIONAL] - Sampling temperature (0-2)
- `maxOutputTokens`: integer [OPTIONAL] - Max tokens
- `topP`: number [OPTIONAL] - Nucleus sampling
- `topK`: integer [OPTIONAL] - Top K sampling
- `stopSequences`: array [OPTIONAL] - Stop sequences

## Example Request Bodies

**Generate Content:**
```json
{"contents": [{"parts": [{"text": "Write a story about a robot"}]}], "generationConfig": {"temperature": 0.9, "maxOutputTokens": 1000}}
```

**Multimodal (with image):**
```json
{"contents": [{"parts": [{"text": "What's in this image?"}, {"inlineData": {"mimeType": "image/jpeg", "data": "BASE64_ENCODED_IMAGE"}}]}], "generationConfig": {"temperature": 0.4}}
```

**Count Tokens:**
```json
{"contents": [{"parts": [{"text": "Hello world"}]}]}
```

**Embeddings:**
```json
{"content": {"parts": [{"text": "The quick brown fox"}]}}
```
