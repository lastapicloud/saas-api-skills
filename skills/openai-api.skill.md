---
name: openai-api
description: Generate text, embeddings, and images via OpenAI API. Use when the user
  mentions openai, gpt, chat, completion, embedding, image, dall-e, ai.
version: 1.0.0
skill_type: external
base_url_env: OPENAI_API_BASE_URL
auth_env_var: OPENAI_API_KEY
auth_type: bearer
triggers:
  - openai
  - gpt
  - chat
  - completion
  - embedding
  - image
  - dall-e
  - ai
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires OPENAI_API_BASE_URL and OPENAI_API_KEY environment variables.
---

# Openai-Api

Generate text, embeddings, and images via OpenAI API. Use when the user mentions openai, gpt, chat, completion, embedding, image, dall-e, ai.

## API Endpoints

- **POST** `/v1/chat/completions` - Create chat completion
- **POST** `/v1/completions` - Create completion
- **POST** `/v1/embeddings` - Create embeddings
- **POST** `/v1/images/generations` - Generate image
- **GET** `/v1/models` - List models
- **GET** `/v1/models/{model}` - Get model
- **POST** `/v1/audio/transcriptions` - Transcribe audio
- **POST** `/v1/moderations` - Create moderation
- **GET** `/files` - Returns a list of files that belong to the user's organization.
- **POST** `/files` - Upload a file that contains document(s) to be used across various endpoints/features. Currently, the size of all the
- **DELETE** `/files/{file_id}` - Delete a file.
- **GET** `/fine-tunes` - List your organization's fine-tuning jobs
- **POST** `/fine-tunes` - Creates a job that fine-tunes a specified model from a given dataset.
- **GET** `/models` - Lists the currently available models, and provides basic information about each one such as the owner and availability.
- **GET** `/models/{model}` - Retrieves a model instance, providing basic information about the model such as the owner and permissioning.

## Actions

- create: Create chat completion (POST /v1/chat/completions)
- create_completions: Create completion (POST /v1/completions)
- create_embeddings: Create embeddings (POST /v1/embeddings)
- create_generations: Generate image (POST /v1/images/generations)
- list: List models (GET /v1/models)
- get_by_id: Get model (GET /v1/models/{model})
- create_transcriptions: Transcribe audio (POST /v1/audio/transcriptions)
- create_moderations: Create moderation (POST /v1/moderations)
- list_files: Returns a list of files that belong to the user's organization. (GET /files)
- create_files: Upload a file that contains document(s) to be used across various endpoints/feat (POST /files)
- delete: Delete a file. (DELETE /files/{file_id})
- list_fine_tunes: List your organization's fine-tuning jobs (GET /fine-tunes)
- create_fine_tunes: Creates a job that fine-tunes a specified model from a given dataset. (POST /fine-tunes)
- list_models: Lists the currently available models, and provides basic information about each (GET /models)
- get_by_id_models: Retrieves a model instance, providing basic information about the model such as (GET /models/{model})

## Fields

- `model`: string [REQUIRED]
- `messages`: array [REQUIRED for chat]
- `prompt`: string [REQUIRED for complete/image]
- `input`: string [REQUIRED for embed]

## Example Request Bodies

**Create Chat Completion:**
```json
{"model": "gpt-4o", "messages": [{"role": "system", "content": "You are a helpful assistant."}, {"role": "user", "content": "Explain REST APIs"}]}
```

**Create Embeddings:**
```json
{"model": "text-embedding-3-small", "input": "Sample text for embedding"}
```
