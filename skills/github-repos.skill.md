---
name: github-repos
description: "Complete GitHub API integration \u2014 repositories, issues, pull requests,\
  \ branches, commits, actions/workflows, releases, organizations, users, gists, and\
  \ search. Use when the user mentions github, repo, repository, issue, pull request,\
  \ PR, commit, code, branch, release, workflow, actions, gist, organization, org,\
  \ merge, fork, collaborator, milestone, label."
version: 1.0.0
skill_type: external
base_url_env: GITHUB_API_BASE_URL
auth_env_var: GITHUB_API_TOKEN
auth_type: bearer
triggers:
  - github
  - repo
  - repository
  - issue
  - pull request
  - PR
  - commit
  - code
license: Apache-2.0
metadata:
  author: lastapi
  version: 2.0.0
compatibility: Requires GITHUB_API_BASE_URL and GITHUB_API_TOKEN environment variables.
---

# Github-Repos

Complete GitHub API integration — repositories, issues, pull requests, branches, commits, actions/workflows, releases, organizations, users, gists, and search. Use when the user mentions github, repo, repository, issue, pull request, PR, commit, code, branch, release, workflow, actions, gist, organization, org, merge, fork, collaborator, milestone, label.

## API Endpoints

- **GET** `/user/repos` - List authenticated user's repositories
- **GET** `/repos/{owner}/{repo}` - Get a repository
- **POST** `/user/repos` - Create a repository for the authenticated user
- **PATCH** `/repos/{owner}/{repo}` - Update a repository
- **DELETE** `/repos/{owner}/{repo}` - Delete a repository
- **POST** `/repos/{owner}/{repo}/forks` - Create a fork
- **GET** `/repos/{owner}/{repo}/forks` - List forks
- **GET** `/repos/{owner}/{repo}/collaborators` - List collaborators
- **PUT** `/repos/{owner}/{repo}/collaborators/{username}` - Add a collaborator
- **DELETE** `/repos/{owner}/{repo}/collaborators/{username}` - Remove a collaborator
- **GET** `/repos/{owner}/{repo}/contents/{path}` - Get file contents
- **PUT** `/repos/{owner}/{repo}/contents/{path}` - Create or update file contents
- **GET** `/repos/{owner}/{repo}/topics` - Get repository topics
- **PUT** `/repos/{owner}/{repo}/topics` - Replace repository topics
- **GET** `/repos/{owner}/{repo}/issues` - List issues

## Actions

- list: List authenticated user's repositories (GET /user/repos)
- get_by_id: Get a repository (GET /repos/{owner}/{repo})
- create: Create a repository for the authenticated user (POST /user/repos)
- update: Update a repository (PATCH /repos/{owner}/{repo})
- delete: Delete a repository (DELETE /repos/{owner}/{repo})
- create_forks: Create a fork (POST /repos/{owner}/{repo}/forks)
- list_forks: List forks (GET /repos/{owner}/{repo}/forks)
- list_collaborators: List collaborators (GET /repos/{owner}/{repo}/collaborators)
- update_collaborators: Add a collaborator (PUT /repos/{owner}/{repo}/collaborators/{username})
- delete_collaborators: Remove a collaborator (DELETE /repos/{owner}/{repo}/collaborators/{username})
- get_by_id_contents: Get file contents (GET /repos/{owner}/{repo}/contents/{path})
- update_contents: Create or update file contents (PUT /repos/{owner}/{repo}/contents/{path})
- list_topics: Get repository topics (GET /repos/{owner}/{repo}/topics)
- put_topics: Replace repository topics (PUT /repos/{owner}/{repo}/topics)
- list_issues: List issues (GET /repos/{owner}/{repo}/issues)

## Fields

### Repository
- `name`: string [REQUIRED for create] - Repository name
- `description`: string [OPTIONAL] - Short description
- `homepage`: string [OPTIONAL] - URL with more info
- `private`: boolean [OPTIONAL] - Whether the repo is private (default false)
- `has_issues`: boolean [OPTIONAL] - Enable issues (default true)
- `has_projects`: boolean [OPTIONAL] - Enable projects (default true)
- `has_wiki`: boolean [OPTIONAL] - Enable wiki (default true)
- `auto_init`: boolean [OPTIONAL] - Initialize with README (default false)
- `gitignore_template`: string [OPTIONAL] - .gitignore template name (e.g., "Python", "Node")
- `license_template`: string [OPTIONAL] - License keyword (e.g., "mit", "apache-2.0")
- `allow_squash_merge`: boolean [OPTIONAL] - Allow squash merging (default true)
- `allow_merge_commit`: boolean [OPTIONAL] - Allow merge commits (default true)
- `allow_rebase_merge`: boolean [OPTIONAL] - Allow rebase merging (default true)
- `delete_branch_on_merge`: boolean [OPTIONAL] - Auto-delete head branches after merge (default false)
- `default_branch`: string [OPTIONAL] - Default branch name (for update only)
- `visibility`: string [OPTIONAL] - public, private, or internal (for org repos)

### Issue
- `title`: string [REQUIRED for create] - Issue title
- `body`: string [OPTIONAL] - Issue body (Markdown supported)
- `assignees`: array of strings [OPTIONAL] - Usernames to assign
- `milestone`: integer [OPTIONAL] - Milestone number to associate
- `labels`: array of strings [OPTIONAL] - Label names to apply
- `state`: string [OPTIONAL for update] - open or closed
- `state_reason`: string [OPTIONAL for update] - completed, not_planned, or reopened

### Pull Request
- `title`: string [REQUIRED for create] - PR title
- `body`: string [OPTIONAL] - PR description (Markdown supported)
- `head`: string [REQUIRED for create] - Branch with changes (e.g., "feature-branch" or "user:feature-branch" for cross-repo)
- `base`: string [REQUIRED for create] - Target branch (e.g., "main")
- `draft`: boolean [OPTIONAL] - Create as draft PR (default false)
- `maintainer_can_modify`: boolean [OPTIONAL] - Allow maintainer edits (default true)
- `state`: string [OPTIONAL for update] - open or closed
- `merge_method`: string [OPTIONAL for merge] - merge, squash, or rebase
- `commit_title`: string [OPTIONAL for merge] - Custom merge commit title
- `commit_message`: string [OPTIONAL for merge] - Custom merge commit message
- `sha`: string [OPTIONAL for merge] - Head SHA to ensure PR has not been updated

### Pull Request Review
- `event`: string [REQUIRED for create] - APPROVE, REQUEST_CHANGES, or COMMENT
- `body`: string [REQUIRED if REQUEST_CHANGES or COMMENT] - Review body text
- `comments`: array [OPTIONAL] - Inline comments, each with `path`, `position`, and `body`

### Branch Protection
- `required_status_checks`: object [OPTIONAL] - {strict: boolean, contexts: array of strings}
- `enforce_admins`: boolean [OPTIONAL] - Enforce rules for admins too
- `required_pull_request_reviews`: object [OPTIONAL] - {required_approving_review_count: integer, dismiss_stale_reviews: boolean}
- `restrictions`: object [OPTIONAL] - {users: array, teams: array} - Restrict who can push
- `allow_force_pushes`: boolean [OPTIONAL] - Allow force pushes (default false)
- `allow_deletions`: boolean [OPTIONAL] - Allow branch deletion (default false)
- `required_linear_history`: boolean [OPTIONAL] - Require linear history (default false)

### Release
- `tag_name`: string [REQUIRED for create] - Tag name (e.g., "v1.0.0")
- `target_commitish`: string [OPTIONAL] - Branch or commit SHA for the tag (default: default branch)
- `name`: string [OPTIONAL] - Release title
- `body`: string [OPTIONAL] - Release notes (Markdown supported)
- `draft`: boolean [OPTIONAL] - Create as draft (default false)
- `prerelease`: boolean [OPTIONAL] - Mark as pre-release (default false)
- `generate_release_notes`: boolean [OPTIONAL] - Auto-generate release notes (default false)

### Label
- `name`: string [REQUIRED for create] - Label name
- `color`: string [OPTIONAL] - Hex color code without # (e.g., "ff0000")
- `description`: string [OPTIONAL] - Short description

### Milestone
- `title`: string [REQUIRED for create] - Milestone title
- `state`: string [OPTIONAL] - open or closed (default open)
- `description`: string [OPTIONAL] - Description
- `due_on`: string [OPTIONAL] - Due date (ISO 8601 timestamp, e.g., "2026-12-31T23:59:59Z")

### Gist
- `description`: string [OPTIONAL] - Gist description
- `public`: boolean [OPTIONAL] - Whether the gist is public (default false)
- `files`: object [REQUIRED for create] - Map of filename to {content: string}

### Workflow Dispatch
- `ref`: string [REQUIRED] - Branch or tag to run the workflow on
- `inputs`: object [OPTIONAL] - Key-value map of workflow input parameters

### File Content (Create/Update)
- `message`: string [REQUIRED] - Commit message
- `content`: string [REQUIRED] - Base64-encoded file content
- `sha`: string [REQUIRED for update] - SHA of the file being replaced
- `branch`: string [OPTIONAL] - Branch to commit to (default: default branch)
- `committer`: object [OPTIONAL] - {name: string, email: string}

### Common Query Parameters (for list endpoints)
- `per_page`: integer [OPTIONAL] - Results per page (1-100, default 30)
- `page`: integer [OPTIONAL] - Page number (default 1)
- `state`: string [OPTIONAL] - Filter by state: open, closed, all (default varies by endpoint)
- `sort`: string [OPTIONAL] - Sort field (varies by endpoint: created, updated, popularity, etc.)
- `direction`: string [OPTIONAL] - Sort direction: asc or desc
- `since`: string [OPTIONAL] - Filter by date (ISO 8601, e.g., "2026-01-01T00:00:00Z")
- `q`: string [REQUIRED for search] - Search query string

## Example Request Bodies

**Create Repository:**
```json
{"name": "my-new-repo", "description": "A sample repository", "private": true, "auto_init": true, "gitignore_template": "Python", "license_template": "mit"}
```

**Create Issue:**
```json
{"title": "Fix login bug", "body": "The login page returns a 500 error when submitting empty credentials.\n\n## Steps to reproduce\n1. Go to /login\n2. Click submit without entering credentials\n3. Observe 500 error", "labels": ["bug", "high-priority"], "assignees": ["octocat"], "milestone": 1}
```

**Create Pull Request:**
```json
{"title": "Fix login validation", "body": "Resolves #42\n\n## Changes\n- Added client-side validation\n- Added server-side null checks\n\n## Testing\n- Unit tests added for all edge cases", "head": "fix-login", "base": "main", "draft": false}
```

**Merge Pull Request:**
```json
{"merge_method": "squash", "commit_title": "fix: login validation (#42)", "commit_message": "Added client-side and server-side validation for login form."}
```

**Create Pull Request Review:**
```json
{"event": "REQUEST_CHANGES", "body": "A few issues need to be addressed before merging.", "comments": [{"path": "src/login.py", "position": 15, "body": "This null check should also handle empty strings."}]}
```

**Create Release:**
```json
{"tag_name": "v2.0.0", "target_commitish": "main", "name": "Version 2.0.0", "body": "## What's Changed\n- New authentication system\n- Performance improvements\n- Bug fixes\n\n**Full Changelog**: https://github.com/owner/repo/compare/v1.0.0...v2.0.0", "draft": false, "prerelease": false, "generate_release_notes": true}
```

**Create Gist:**
```json
{"description": "Python utility functions", "public": true, "files": {"utils.py": {"content": "def greet(name):\n    return f'Hello, {name}!'\n"}, "README.md": {"content": "# Utility Functions\nA collection of helper functions."}}}
```

**Create Label:**
```json
{"name": "critical", "color": "ff0000", "description": "Critical issues requiring immediate attention"}
```

**Create Milestone:**
```json
{"title": "v2.0 Release", "state": "open", "description": "All features and fixes targeted for the v2.0 release", "due_on": "2026-06-30T23:59:59Z"}
```

**Trigger Workflow Dispatch:**
```json
{"ref": "main", "inputs": {"environment": "production", "deploy_version": "v2.0.0"}}
```

**Update Branch Protection:**
```json
{"required_status_checks": {"strict": true, "contexts": ["ci/build", "ci/test"]}, "enforce_admins": true, "required_pull_request_reviews": {"required_approving_review_count": 2, "dismiss_stale_reviews": true}, "restrictions": null, "allow_force_pushes": false, "allow_deletions": false, "required_linear_history": true}
```

**Create or Update File Contents:**
```json
{"message": "Add configuration file", "content": "eyJrZXkiOiAidmFsdWUifQ==", "branch": "main", "committer": {"name": "Octocat", "email": "octocat@github.com"}}
```

**Search Code (Query Params):**
Query parameter: `q=addClass+in:file+language:js+repo:jquery/jquery`

**Search Repositories (Query Params):**
Query parameter: `q=tetris+language:python+stars:>100&sort=stars&order=desc`

**Search Issues (Query Params):**
Query parameter: `q=bug+label:bug+state:open+repo:owner/repo&sort=created&order=desc`
