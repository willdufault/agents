---
name: code-review2
description: Use when reviewing code for KISS, DRY, YAGNI issues.
---

Run one subagent per section that verifies each finding and returns one table per section: ID (K1, D1, Y1), file:line, issue, fix. Fixes must not change behavior and must make code simpler.

## KISS
- Verbose code; shorter is better
- Complex or clever logic
- Needless abstraction

## DRY
- Code duplicated 3+ times

## YAGNI
- Dead, unused, speculative code
- Exempt: defensive checks, type/lint narrowing, input validation, user-facing behavior
