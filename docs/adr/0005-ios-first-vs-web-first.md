# ADR 0005: Epic order, iOS first (reversed and re-reversed)

## Status
Accepted

## Context
Epic order was originally set as iOS App (core) → AR/ML → Web Twin, since the iOS client was the primary resume signal. Partway into planning, it came to light that no Mac was available for local iOS development. Since Vapor runs natively on Linux/Windows (official Swift toolchain, no Xcode required for server-side Swift) but SwiftUI compiles only through Xcode, the plan was temporarily restructured to Web + Backend → iOS Twin → AR/ML, so backend and web work could start immediately without a hardware blocker.

That restructuring was reverted once Mac access was resolved via an AWS EC2 Mac instance (see ADR-0006), removing the original blocker.

## Decision
Epic order reverted to the original: iOS App (core build) → AR/ML enhancements → Web Twin (React).

## Consequences
No lasting architectural cost from the detour, the planning work done during the web-first pivot (date-range/overlap-checking logic, accessibility approach, logging strategy) applied equally well once the order reverted, since those are cross-cutting concerns rather than platform-specific ones. Left in the ADR log intentionally: real projects change direction when new constraints surface, and reversing a decision cleanly when the underlying blocker resolves is itself worth documenting.
