---
name: huggingface-inference
description: Run inference tasks via Hugging Face API. Use when the user mentions
  hugging face, huggingface, inference, model, nlp, text generation, embedding.
version: 1.0.0
skill_type: external
base_url_env: HUGGINGFACE_INFERENCE_BASE_URL
auth_env_var: HUGGINGFACE_INFERENCE_API_KEY
auth_type: bearer
triggers:
  - hugging face
  - huggingface
  - inference
  - model
  - nlp
  - text generation
  - embedding
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires HUGGINGFACE_INFERENCE_BASE_URL and HUGGINGFACE_INFERENCE_API_KEY
  environment variables.
---

# Huggingface-Inference

Run inference tasks via Hugging Face API. Use when the user mentions hugging face, huggingface, inference, model, nlp, text generation, embedding.

## API Endpoints

- **POST** `/models/{model_id}` - Run inference
- **GET** `/models` - List models
- **GET** `/models/{model_id}` - Get model info
- **POST** `/pipeline/text-generation` - Text generation
- **POST** `/pipeline/feature-extraction` - Feature extraction
- **POST** `/pipeline/text-classification` - Text classification
- **POST** `/pipeline/summarization` - Summarization

## Actions

- create_models: Run inference (POST /models/{model_id})
- list: List models (GET /models)
- get_by_id: Get model info (GET /models/{model_id})
- create: Text generation (POST /pipeline/text-generation)
- create_feature_extraction: Feature extraction (POST /pipeline/feature-extraction)
- create_text_classification: Text classification (POST /pipeline/text-classification)
- create_summarization: Summarization (POST /pipeline/summarization)

## Fields

- `inputs`: string [REQUIRED for inference]
- `model_id`: string [REQUIRED]
- `parameters`: object [OPTIONAL]

## Example Request Bodies

**Text Generation:**
```json
{"inputs": "Once upon a time", "model_id": "meta-llama/Llama-3.1-70B-Instruct", "parameters": {"max_new_tokens": 200}}
```

**Text Classification:**
```json
{"inputs": "This movie was absolutely fantastic!", "model_id": "distilbert-base-uncased-finetuned-sst-2-english"}
```
