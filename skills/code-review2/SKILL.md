---
name: code-review2
description: Use when reviewing code for KISS, DRY, YAGNI issues.
---

Run one subagent per section. Each verifies its finding, keeps only clear wins, and returns one table per section: ID (K1, D1, Y1), file:line, issue, fix. Fixes must make code simpler and must not change behavior.

## KISS
- Verbose code; shorter is better
- Complex or clever logic
- Needless abstraction

## DRY
- Logic duplicated 3+ times

## YAGNI
- Dead, unused, speculative code
- Exempt: defensive checks, type/lint narrowing, input validation, user-facing behavior
