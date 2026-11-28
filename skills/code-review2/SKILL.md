---
name: code-review2
description: Use when reviewing code for KISS, DRY, YAGNI issues.
---

Run one subagent per section. It verifies each finding before reporting and returns a table: ID, file:line, issue, fix. IDs are the section's initial plus a number: K1, D1, Y1. Report one table per section. Fixes must not change behavior.

## KISS
- Verbose code; shorter is better
- Complex or clever logic
- Needless abstraction

## DRY
- Logic, constants, types, helpers duplicated 3+ times

## YAGNI
- Dead, unused, speculative code
- Exempt: defensive checks, type/lint narrowing, input validation, user-facing behavior
