---
name: azure-openai
description: Azure OpenAI LLM API. Use when the user mentions azure openai, azure AI, microsoft AI, Azure Foundry.
version: 1.0.0
skill_type: external
base_url_env: AZURE_OPENAI_BASE_URL
auth_env_var: AZURE_OPENAI_API_KEY
auth_type: bearer
triggers:
  - azure openai
  - azure AI
  - microsoft AI
  - Azure Foundry
license: Proprietary
metadata:
  author: lastapi
  version: 1.0.0
  documentation: https://learn.microsoft.com/azure/ai-services/openai/
---

# Azure-OpenAI

Azure OpenAI LLM API. Use when the user mentions azure openai, azure AI, microsoft AI, Azure Foundry.

## API Endpoints

- **POST** `/openai/chat/completions?api-version=2024-02-01` - Create chat completion
- **POST** `/openai/completions?api-version=2024-02-01` - Create text completion
- **GET** `/openai/models?api-version=2024-02-01` - List available models
- **POST** `/openai/embeddings?api-version=2024-02-01` - Generate embeddings
- **POST** `/openai/images/generations?api-version=2024-02-01` - Generate images
- **POST** `/openai/audio/transcriptions?api-version=2024-02-01` - Speech to text

## Actions

- create_chat: Create chat completion (POST /openai/chat/completions)
- create_completion: Create text completion (POST /openai/completions)
- list_models: List available models (GET /openai/models)
- create_embedding: Generate embeddings (POST /openai/embeddings)
- generate_image: Generate images (POST /openai/images/generations)
- transcribe: Speech to text (POST /openai/audio/transcriptions)

## Fields

- `model`: string [REQUIRED] - Model deployment name
- `messages`: array [REQUIRED for chat] - Chat messages
- `prompt`: string [REQUIRED for completion] - Text prompt
- `temperature`: number [OPTIONAL] - Sampling temperature (0-2)
- `max_tokens`: integer [OPTIONAL] - Max tokens
- `top_p`: number [OPTIONAL] - Nucleus sampling
- `stream`: boolean [OPTIONAL] - Stream responses
- `deployment_name`: string [REQUIRED for embeddings] - Embeddings deployment

## Example Request Bodies

**Chat Completion:**
```json
{"model": "gpt-4", "messages": [{"role": "user", "content": "Hello world"}]}
```

**Embeddings:**
```json
{"input": "The quick brown fox", "model": "text-embedding-ada-002"}
```
