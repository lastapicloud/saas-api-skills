---
name: replicate-ai
description: Run AI models via Replicate. Use when the user mentions replicate, ai,
  model, prediction, inference, image generation.
version: 1.0.0
skill_type: external
base_url_env: REPLICATE_BASE_URL
auth_env_var: REPLICATE_API_TOKEN
auth_type: bearer
triggers:
  - replicate
  - ai
  - model
  - prediction
  - inference
  - image generation
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires REPLICATE_BASE_URL and REPLICATE_API_TOKEN environment variables.
---

# Replicate-Ai

Run AI models via Replicate. Use when the user mentions replicate, ai, model, prediction, inference, image generation.

## API Endpoints

- **POST** `/v1/predictions` - Create prediction
- **GET** `/v1/predictions/{id}` - Get prediction
- **POST** `/v1/predictions/{id}/cancel` - Cancel prediction
- **GET** `/v1/predictions` - List predictions
- **GET** `/v1/models` - List models
- **GET** `/v1/models/{owner}/{name}` - Get model
- **GET** `/v1/models/{owner}/{name}/versions` - List model versions
- **GET** `/v1/collections` - List collections

## Actions

- create: Create prediction (POST /v1/predictions)
- get_by_id: Get prediction (GET /v1/predictions/{id})
- create_cancel: Cancel prediction (POST /v1/predictions/{id}/cancel)
- list: List predictions (GET /v1/predictions)
- list_models: List models (GET /v1/models)
- get_by_id_models: Get model (GET /v1/models/{owner}/{name})
- list_versions: List model versions (GET /v1/models/{owner}/{name}/versions)
- list_collections: List collections (GET /v1/collections)

## Fields

- `version`: string [REQUIRED for create]
- `input`: object [REQUIRED for create]

## Example Request Bodies

**Create Prediction:**
```json
{"version": "a]b12c3d4e5f6", "input": {"prompt": "A photo of an astronaut riding a horse", "num_outputs": 1}}
```

**Cancel Prediction:**
```json
{}
