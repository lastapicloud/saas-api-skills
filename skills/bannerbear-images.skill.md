---
name: bannerbear-images
description: Auto-generate images and videos via Bannerbear. Use when the user mentions bannerbear, image generation, video generation, design automation, template, marketing.
version: 1.0.0
skill_type: external
base_url_env: BANNERBEAR_BASE_URL
auth_env_var: BANNERBEAR_API_KEY
auth_type: bearer
triggers:
  - bannerbear
  - image generation
  - video generation
  - design automation
  - template
  - marketing
license: Proprietary
metadata:
  author: lastapi
  version: 1.0.0
  api_version: v2
---

# Bannerbear-Images

Auto-generate images and videos via Bannerbear. Use when the user mentions bannerbear, image generation, video generation, design automation, template, marketing.

## API Endpoints

- **GET** `/v2/account` - Get account status and quota
- **GET** `/v2/auth` - Verify authentication
- **POST** `/v2/images` - Create a new image
- **GET** `/v2/images/:uid` - Get image by UID
- **GET** `/v2/images` - List all images
- **POST** `/v2/videos` - Create a new video
- **GET** `/v2/videos/:uid` - Get video by UID
- **GET** `/v2/videos` - List all videos
- **PATCH** `/v2/videos` - Update video (transcription, approval)
- **POST** `/v2/collections` - Create a collection (multiple images)
- **GET** `/v2/collections/:uid` - Get collection by UID
- **GET** `/v2/collections` - List all collections
- **POST** `/v2/animated_gifs` - Create an animated GIF
- **GET** `/v2/animated_gifs/:uid` - Get animated GIF by UID
- **GET** `/v2/animated_gifs` - List all animated GIFs
- **POST** `/v2/screenshots` - Create a screenshot
- **GET** `/v2/screenshots/:uid` - Get screenshot by UID
- **GET** `/v2/screenshots` - List all screenshots
- **GET** `/v2/templates` - List templates
- **GET** `/v2/templates/:uid` - Get template by UID
- **POST** `/v2/templates` - Create a blank template
- **PATCH** `/v2/templates/:uid` - Update template
- **DELETE** `/v2/templates/:uid` - Delete template

## Actions

- get_account: Get account status and quota (GET /v2/account)
- verify_auth: Verify authentication (GET /v2/auth)
- create_image: Create a new image (POST /v2/images)
- get_image: Get image by UID (GET /v2/images/:uid)
- list_images: List all images (GET /v2/images)
- create_video: Create a new video (POST /v2/videos)
- get_video: Get video by UID (GET /v2/videos/:uid)
- list_videos: List all videos (GET /v2/videos)
- update_video: Update video (PATCH /v2/videos)
- create_collection: Create a collection (POST /v2/collections)
- get_collection: Get collection by UID (GET /v2/collections/:uid)
- list_collections: List all collections (GET /v2/collections)
- create_animated_gif: Create an animated GIF (POST /v2/animated_gifs)
- get_animated_gif: Get animated GIF by UID (GET /v2/animated_gifs/:uid)
- list_animated_gifs: List all animated GIFs (GET /v2/animated_gifs)
- create_screenshot: Create a screenshot (POST /v2/screenshots)
- get_screenshot: Get screenshot by UID (GET /v2/screenshots/:uid)
- list_screenshots: List all screenshots (GET /v2/screenshots)
- list_templates: List templates (GET /v2/templates)
- get_template: Get template by UID (GET /v2/templates/:uid)
- create_template: Create a blank template (POST /v2/templates)
- update_template: Update template (PATCH /v2/templates/:uid)
- delete_template: Delete template (DELETE /v2/templates/:uid)

## Fields

- `template`: string [REQUIRED for create] - Template UID
- `modifications`: array [REQUIRED for create] - List of modifications
- `webhook_url`: string [OPTIONAL] - Webhook URL for completion notification
- `transparent`: boolean [OPTIONAL] - Render PNG with transparent background
- `render_pdf`: boolean [OPTIONAL] - Render PDF (costs 3x quota)
- `metadata`: string [OPTIONAL] - Any metadata to store
- `text`: string [OPTIONAL in modifications] - Text replacement
- `image_url`: string [OPTIONAL in modifications] - Image URL replacement

## Example Request Bodies

**Create Image:**
```json
{"template": "TEMPLATE_UID", "modifications": [{"name": "title", "text": "Hello World"}, {"name": "photo", "image_url": "https://example.com/photo.jpg"}]}
```

**Create Video:**
```json
{"video_template": "VIDEO_TEMPLATE_UID", "input_media_url": "https://example.com/video.mp4", "modifications": [{"name": "subtitle", "text": "Hello World"}]}
```

**Create Collection:**
```json
{"template_set": "TEMPLATE_SET_UID", "modifications": [{"name": "title", "text": "Hello World"}]}
```
