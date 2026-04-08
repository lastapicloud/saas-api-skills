---
name: groq-ai
description: Fast LLM inference via Groq. Use when the user mentions groq, fast inference, low latency, high throughput, LLM API.
version: 1.0.0
skill_type: external
base_url_env: GROQ_BASE_URL
auth_env_var: GROQ_API_KEY
auth_type: bearer
triggers:
  - groq
  - fast inference
  - low latency
  - high throughput
  - LLM API
license: Proprietary
metadata:
  author: lastapi
  version: 1.0.0
  documentation: https://console.groq.com/docs
---

# Groq-AI

Fast LLM inference via Groq. Use when the user mentions groq, fast inference, low latency, high throughput, LLM API.

## API Endpoints

- **POST** `/openai/v1/chat/completions` - Create chat completion
- **POST** `/openai/v1/completions` - Create text completion
- **GET** `/openai/v1/models` - List available models
- **GET** `/openai/v1/models/{model}` - Get model information
- **POST** `/openai/v1/audio/transcriptions` - Speech to text
- **POST** `/openai/v1/embeddings` - Generate embeddings

## Actions

- create_chat: Create chat completion (POST /openai/v1/chat/completions)
- create_completion: Create text completion (POST /openai/v1/completions)
- list_models: List available models (GET /openai/v1/models)
- get_model: Get model information (GET /openai/v1/models/{model})
- transcribe: Speech to text (POST /openai/v1/audio/transcriptions)
- create_embedding: Generate embeddings (POST /openai/v1/embeddings)

## Fields

- `model`: string [REQUIRED] - Model name (e.g., llama-3.3-70b, mixtral-8x7b)
- `messages`: array [REQUIRED for chat] - Chat messages
- `prompt`: string [REQUIRED for completion] - Text prompt
- `temperature`: number [OPTIONAL] - Sampling temperature (0-2)
- `max_tokens`: integer [OPTIONAL] - Max tokens to generate
- `top_p`: number [OPTIONAL] - Nucleus sampling
- `stream`: boolean [OPTIONAL] - Stream responses
- `response_format`: object [OPTIONAL] - Response format (json_schema)
- `tools`: array [OPTIONAL] - Function calling tools

## Example Request Bodies

**Chat Completion:**
```json
{"model": "llama-3.3-70b-versatile", "messages": [{"role": "user", "content": "What is machine learning?"}], "temperature": 0.7, "max_tokens": 500}
```

**Text Completion:**
```json
{"model": "llama-3.3-70b-versatile", "prompt": "Once upon a time", "temperature": 0.7, "max_tokens": 100}
```

**Structured Output:**
```json
{"model": "llama-3.3-70b-versatile", "messages": [{"role": "user", "content": "List 3 programming languages"}], "response_format": {"type": "json_object"}}
```
