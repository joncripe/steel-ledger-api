# CLAUDE.md

Context for Claude Code working in this repo. Keep this file thin, practical,
and current. Full project narrative lives elsewhere, don't duplicate it here.

## What this repo is
Vapor (Swift) backend for **The Steel Ledger**, an armor/weapon loan-tracking
app for Buhurt teams. REST API shared by the iOS app (`steel-ledger-ios`) and
future web client (`steel-ledger-web`).

## Where the "why" lives
- **Full project scope, MVP definition, epics, data model**: [Confluence — The
  Steel Ledger Project Scope](https://joncripe.atlassian.net/wiki/spaces/TSL/pages/66041)
- **Architecture decisions and reasoning (API/code only — infra decisions
  moved to `steel-ledger-infra`)**: [`/docs/adr`](./docs/adr)
- **Ticket tracking**: Jira project `TSL`, Epic 1 = `TSL-4`

Don't re-derive or restate reasoning from those sources here, link to them.

## Stack
- Vapor (Swift), Fluent ORM for CRUD, raw SQL for the FitMatch query
  (see [ADR-0001](./docs/adr/0001-fluent-vs-raw-sql.md))
- Postgres, local via `docker-compose`, production via AWS RDS
- Terraform for AWS infra (RDS, App Runner, Secrets Manager, S3)
- Sign in with Apple for auth (see [ADR-0003](./docs/adr/0003-sign-in-with-apple.md))

## Local development
> To be filled in once the Vapor scaffold exists (Weekend 1 / TSL-1). Will cover:
> `docker-compose up` for local Postgres, `.env` setup, `swift run`.

## Conventions
- Branch naming, commit style, PR process: see [`CONTRIBUTING.md`](./CONTRIBUTING.md)
- Linting: `swift-format lint --recursive Sources/ Tests/` before committing
- New architecturally-significant decision? Add an ADR to `/docs/adr`, don't
  just describe it in a PR and let the reasoning disappear into history

## Current status
Pre-scaffold. Epic 1, Weekend 1 (TSL-1: Vapor skeleton + Postgres/Fluent
connection) has not started yet. Update this section as work progresses.
