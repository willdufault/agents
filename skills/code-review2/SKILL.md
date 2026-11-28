---
name: code-review2
description: Use when reviewing code for KISS, DRY, YAGNI issues.
---

Run one subagent per section. It verifies each finding before reporting and returns a table: file:line, issue, fix. Fixes must not change behavior.

## KISS
- Fewer lines; each is a liability
- Complex or clever logic
- Needless abstraction

## DRY
- Duplicated logic, constants, types, helpers

## YAGNI
- Dead, unused, speculative code
- Impossible cases; cite why
- Exempt: type/lint narrowing, input validation, user-facing behavior
