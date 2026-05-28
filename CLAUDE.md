# CLAUDE.md — saas-api-skills

> **Public** repo. Curated catalog of 368+ API integration skills following the [agentskills.io](https://agentskills.io/specification) spec. Sub-repo of the LastAPI workspace; root router: `../CLAUDE.md`. README owns the marketing-side narrative — this file owns the engineering / contributor view.

## What This Is

A community-oriented index of `*.skill.md` files, each describing how an AI agent (Claude, GPT, generic LLM) should call a specific SaaS HTTP API: endpoints, parameters, auth, example payloads. Used by:

- `lastapi-framework` `/assistant/*` routes — every customer Lambda's auto-generated Skill Loader pulls from this catalog at deploy time
- `lastapi-frontend` integrations browser — surfaces metadata for the 387 integrations the dashboard offers
- External agents — anyone running an MCP-style agent can clone this repo and load the skill files

Single source of truth: the `skills/` directory. Everything else (README badges, license, contributor docs) is metadata around that.

## Stack

- **No runtime** — pure markdown collection, no build step, no package.json
- **Spec:** [agentskills.io](https://agentskills.io/specification) — each `*.skill.md` follows the documented frontmatter + section schema
- **Hosting:** GitHub `lastapicloud/saas-api-skills` (public, MIT licensed)

## Architecture

```
saas-api-skills
  ├── skills/                 — 368 *.skill.md files (one per service)
  │   ├── stripe-payments.skill.md
  │   ├── slack-messaging.skill.md
  │   ├── notion-pages.skill.md
  │   └── ... 365 more
  ├── README.md               — public-facing catalog overview + quick start
  ├── CONTRIBUTING.md         — how to add a new skill
  ├── CODE_OF_CONDUCT.md      — community contract
  └── LICENSE                 — MIT
```

Each `*.skill.md` is self-contained and consumable by an LLM with no external lookups. Categories surface via filename prefix and frontmatter `category` field (Payments, Communication, Productivity, Observability, AI & LLM, etc.).

## Capabilities

- **368+ service integrations** ready for AI-agent consumption (Stripe, Slack, Notion, Datadog, OpenAI, …)
- **Spec-compliant** — follows agentskills.io specification, so any compliant agent runtime can load these without per-skill custom code
- **Versioned via git** — every skill file's history is the audit trail
- **Public + community-extensible** — accepts PRs from external contributors per CONTRIBUTING.md

## Public Surface

| Surface | Where |
|---|---|
| Catalog browse | [`skills/`](skills/) directory + README's example table |
| Direct skill URLs | `https://github.com/lastapicloud/saas-api-skills/blob/main/skills/<name>.skill.md` (raw via `raw.githubusercontent.com/...`) |
| Pulled by | `lastapi-framework` Skill Loader at customer-Lambda deploy time |

No HTTP API of its own — consumers fetch raw files from GitHub.

## Scopes

- **Public — open source under MIT.** External contributors welcome.
- **Catalog scope:** SaaS HTTP APIs that an AI agent might call. Not for SDK-style libraries, not for non-HTTP protocols.
- **Spec-bound:** any file in `skills/` MUST follow agentskills.io. Use CONTRIBUTING.md as the gate.
- **Customer-Lambda contract:** changes here ripple into every deployed customer API at next deploy time. Treat schema-incompatible changes as breaking and version them deliberately.

## Repo

- **GitHub:** `lastapicloud/saas-api-skills` (PUBLIC)
- **License:** MIT
- **Default branch:** `main`
- **Branch protection:** none (open contribution model)
- **CI:** none today — skill files validated by reviewers + downstream consumers

## Cross-Repo Dependencies

```
saas-api-skills (this repo)
  ↓ consumed by
lastapi-framework  ← Skill Loader injects skills into every customer Lambda at deploy
  ↓
customer Lambdas   ← /assistant/skills exposes the loaded catalog at runtime
```

## Workflow

```bash
# Add a new skill
git checkout -b add-<service-name>-skill
# Author skills/<service>-<surface>.skill.md following agentskills.io
# README + CONTRIBUTING.md describe the schema in full
git commit -m "add(<service>): <surface> skill"
gh pr create --base main
```

## Rules

- Every skill must follow [agentskills.io](https://agentskills.io/specification) spec exactly — frontmatter + section ordering + parameter shape.
- Filename pattern: `<service>-<primary-surface>.skill.md` (lowercase, hyphenated, e.g. `stripe-payments.skill.md`).
- Never embed credentials in examples — use placeholder tokens like `${YOUR_STRIPE_API_KEY}`.
- New category? Update README's example table + add a section if there are 5+ skills in the category.
- Don't force-push `main` — public history is the audit trail for all downstream consumers.
