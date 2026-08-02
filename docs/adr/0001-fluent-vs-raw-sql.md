# ADR 0001: Fluent for CRUD, raw SQL for FitMatch

## Status
Accepted

## Context
Vapor's Fluent ORM is the idiomatic way to interact with Postgres, but the app's standout feature, FitMatch, is a range-matching query (finding Equipment whose FitSpec min/max ranges contain a Member's measurements) that's awkward to express cleanly through an ORM query builder.

## Decision
Use Fluent for standard CRUD (Team, Member, Kit, Equipment, LoanRecord). Drop to raw SQL specifically for the FitMatch query.

## Consequences
Fastest path for the boring parts, CRUD doesn't need hand-tuned SQL. The one place raw SQL is used is also the app's most interesting query, which is a deliberate choice, not a shortcut, and demonstrates both ORM fluency and the ability to write real SQL where it actually matters.
