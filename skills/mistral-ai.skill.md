---
name: mistral-ai
description: AI models via Mistral AI. Use when the user mentions mistral, mistral-ai, codestral, large language model, French AI.
version: 1.0.0
skill_type: external
base_url_env: MISTRAL_BASE_URL
auth_env_var: MISTRAL_API_KEY
auth_type: bearer
triggers:
  - mistral
  - mistral-ai
  - codestral
  - large language model
  - French AI
license: Proprietary
metadata:
  author: lastapi
  version: 1.0.0
  documentation: https://docs.mistral.ai/
---

# Mistral-AI

AI models via Mistral AI. Use when the user mentions mistral, mistral-ai, codestral, large language model, French AI.

## API Endpoints

- **POST** `/v1/chat/completions` - Create chat completion
- **POST** `/v1/completions` - Create text completion
- **GET** `/v1/models` - List available models
- **GET** `/v1/models/{model}` - Get model information
- **POST** `/v1/embeddings` - Generate embeddings
- **POST** `/v1/fine_tuning/jobs` - Create fine-tuning job
- **GET** `/v1/fine_tuning/jobs` - List fine-tuning jobs
- **GET** `/v1/fine_tuning/jobs/{job_id}` - Get fine-tuning job

## Actions

- create_chat: Create chat completion (POST /v1/chat/completions)
- create_completion: Create text completion (POST /v1/completions)
- list_models: List available models (GET /v1/models)
- get_model: Get model information (GET /v1/models/{model})
- create_embedding: Generate embeddings (POST /v1/embeddings)
- create_finetune_job: Create fine-tuning job (POST /v1/fine_tuning/jobs)
- list_finetune_jobs: List fine-tuning jobs (GET /v1/fine_tuning/jobs)
- get_finetune_job: Get fine-tuning job (GET /v1/fine_tuning/jobs/{job_id})

## Fields

- `model`: string [REQUIRED] - Model name (e.g., mistral-large, codestral, pixtral-large)
- `messages`: array [REQUIRED for chat] - Chat messages
- `prompt`: string [REQUIRED for completion] - Text prompt
- `temperature`: number [OPTIONAL] - Sampling temperature (0-2)
- `max_tokens`: integer [OPTIONAL] - Max tokens to generate
- `top_p`: number [OPTIONAL] - Nucleus sampling
- `stream`: boolean [OPTIONAL] - Stream responses
- `tools`: array [OPTIONAL] - Function calling tools
- `response_format`: object [OPTIONAL] - Response format (json_schema)
- `input`: string [REQUIRED for embeddings] - Text to embed
- `training_file`: string [REQUIRED for finetune] - Training file ID

## Example Request Bodies

**Chat Completion:**
```json
{"model": "mistral-large-latest", "messages": [{"role": "user", "content": "What is the capital of France?"}], "temperature": 0.7}
```

**Code Generation:**
```json
{"model": "codestral-latest", "messages": [{"role": "user", "content": "Write a Python function to calculate fibonacci"}], "temperature": 0.3}
```

**Structured Output:**
```json
{"model": "mistral-large-latest", "messages": [{"role": "user", "content": "List 3 fruits"}], "response_format": {"type": "json_object"}}
```

**Embeddings:**
```json
{"input": "The quick brown fox jumps over the lazy dog", "model": "mistral-embed"}
```
