---
name: bitbucket-repos
description: Manage repositories, pull requests, and pipelines via Bitbucket. Use
  when the user mentions bitbucket, repository, pull request, pipeline, branch, commit.
version: 1.0.0
skill_type: external
base_url_env: BITBUCKET_BASE_URL
auth_env_var: BITBUCKET_APP_PASSWORD
auth_user_env: BITBUCKET_USERNAME
auth_type: basic
triggers:
  - bitbucket
  - repository
  - pull request
  - pipeline
  - branch
  - commit
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires BITBUCKET_BASE_URL and BITBUCKET_APP_PASSWORD environment
  variables.
---

# Bitbucket-Repos

Manage repositories, pull requests, and pipelines via Bitbucket. Use when the user mentions bitbucket, repository, pull request, pipeline, branch, commit.

## API Endpoints

- **GET** `/2.0/repositories/{workspace}` - List repositories
- **POST** `/2.0/repositories/{workspace}/{repo_slug}` - Create a repository
- **GET** `/2.0/repositories/{workspace}/{repo_slug}` - Get repository
- **DELETE** `/2.0/repositories/{workspace}/{repo_slug}` - Delete a repository
- **GET** `/2.0/repositories/{workspace}/{repo_slug}/pullrequests` - List pull requests
- **POST** `/2.0/repositories/{workspace}/{repo_slug}/pullrequests` - Create a pull request
- **GET** `/2.0/repositories/{workspace}/{repo_slug}/pipelines` - List pipelines
- **POST** `/2.0/repositories/{workspace}/{repo_slug}/pipelines` - Trigger a pipeline
- **GET** `/snippets` - List snippets
- **POST** `/snippets` - Create a snippet
- **PUT** `/snippets/{workspace}/{encoded_id}` - Update a snippet
- **DELETE** `/snippets/{workspace}/{encoded_id}` - Delete a snippet
- **GET** `/addon/linkers` - List linkers for an app
- **DELETE** `/addon` - Delete an app
- **PUT** `/addon` - Update an installed app

## Actions

- get_by_id: List repositories (GET /2.0/repositories/{workspace})
- add_repositories: Create a repository (POST /2.0/repositories/{workspace}/{repo_slug})
- get_by_id_repositories: Get repository (GET /2.0/repositories/{workspace}/{repo_slug})
- delete: Delete a repository (DELETE /2.0/repositories/{workspace}/{repo_slug})
- list: List pull requests (GET /2.0/repositories/{workspace}/{repo_slug}/pullrequests)
- create: Create a pull request (POST /2.0/repositories/{workspace}/{repo_slug}/pullrequests)
- list_pipelines: List pipelines (GET /2.0/repositories/{workspace}/{repo_slug}/pipelines)
- create_pipelines: Trigger a pipeline (POST /2.0/repositories/{workspace}/{repo_slug}/pipelines)
- list_snippets: List snippets (GET /snippets)
- create_snippets: Create a snippet (POST /snippets)
- update: Update a snippet (PUT /snippets/{workspace}/{encoded_id})
- delete_snippets: Delete a snippet (DELETE /snippets/{workspace}/{encoded_id})
- list_linkers: List linkers for an app (GET /addon/linkers)
- delete_addon: Delete an app (DELETE /addon)
- update_addon: Update an installed app (PUT /addon)

## Fields

- `scm`: string [REQUIRED for create] (git)
- `is_private`: boolean [OPTIONAL]
- `title`: string [REQUIRED for create_pull_request]
- `source`: object [REQUIRED for create_pull_request]

## Example Request Bodies

**Create Repository:**
```json
{"scm": "git", "is_private": true}
```

**Create Pull Request:**
```json
{"title": "Add login feature", "source": {"branch": {"name": "feature/login"}}, "is_private": false}
