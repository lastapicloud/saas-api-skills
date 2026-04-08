---
name: xai-grok
description: xAI Grok AI models. Use when the user mentions xai, grok, grok-2, Elon Musk AI, witty AI, humor.
version: 1.0.0
skill_type: external
base_url_env: XAI_BASE_URL
auth_env_var: XAI_API_KEY
auth_type: bearer
triggers:
  - xai
  - grok
  - grok-2
  - Elon Musk AI
  - witty AI
license: Proprietary
metadata:
  author: lastapi
  version: 1.0.0
  documentation: https://docs.x.ai/
---

# Xai-Grok

xAI Grok AI models. Use when the user mentions xai, grok, grok-2, Elon Musk AI, witty AI, humor.

## API Endpoints

- **POST** `/v1/chat/completions` - Create chat completion
- **POST** `/v1/completions` - Create text completion
- **GET** `/v1/models` - List available models
- **POST** `/v1/images/generations` - Generate images
- **POST** `/v1/images/edits` - Edit images

## Actions

- create_chat: Create chat completion (POST /v1/chat/completions)
- create_completion: Create text completion (POST /v1/completions)
- list_models: List available models (GET /v1/models)
- generate_image: Generate images (POST /v1/images/generations)
- edit_image: Edit images (POST /v1/images/edits)

## Fields

- `model`: string [REQUIRED] - Model name (e.g., grok-2-vision-1212, grok-2-1212)
- `messages`: array [REQUIRED for chat] - Chat messages
- `prompt`: string [REQUIRED for completion] - Text prompt
- `temperature`: number [OPTIONAL] - Sampling temperature (0-2)
- `max_tokens`: integer [OPTIONAL] - Max tokens
- `top_p`: number [OPTIONAL] - Nucleus sampling
- `stream`: boolean [OPTIONAL] - Stream responses
- `n`: integer [OPTIONAL for images] - Number of images to generate

## Example Request Bodies

**Chat Completion:**
```json
{"model": "grok-2-1212", "messages": [{"role": "user", "content": "What is the meaning of life?"}], "temperature": 0.7, "max_tokens": 500}
```

**Text Completion:**
```json
{"model": "grok-2-1212", "prompt": "Write a haiku about AI", "max_tokens": 100, "temperature": 0.8}
```

**Image Generation:**
```json
{"model": "grok-2-image", "prompt": "A cat in space", "n": 1, "size": "1024x1024"}
```
