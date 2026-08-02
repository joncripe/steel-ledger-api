# ADR 0003: Sign in with Apple over a managed auth service

## Status
Accepted

## Context
The app needs auth with minimal account-management overhead. Options considered: Sign in with Apple (identity only, no password storage) and a managed service like Supabase Auth (which would also double as a hosted Postgres layer).

## Decision
Sign in with Apple for identity, verified once at sign-in. Backend mints its own short-lived access JWT plus a refresh token (Keychain on iOS, httpOnly cookie on web), refreshed silently, implemented via `vapor/jwt`.

## Consequences
No password storage, no reset flow, no third-party auth vendor dependency. Re-verifying Apple's identity token on every request was considered and rejected, it would mean re-triggering Apple's native sign-in flow constantly, which is a poor user experience. The self-issued JWT plus refresh token pattern is a small amount of additional code for a meaningfully better experience, and it's a standard, well-understood pattern rather than a shortcut. Also required Terraform for RDS Postgres directly rather than getting it "for free" from a managed auth+DB service like Supabase, a deliberate trade to keep the Terraform/IaC story in the project.
