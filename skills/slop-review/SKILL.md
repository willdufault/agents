---
name: slop-review
description: Use when reviewing code for quality issues and AI slop.
---

1. Run tests.
2. A fresh Opus 5.5 subagent with minimal context reviews the target (whole codebase or given paths) against the criteria. It returns `file:line`, issue and fix for each finding.
3. A second fresh Opus 5.5 subagent verifies each item.
4. Fix the agreed items. Don't edit tests to make them pass.
5. Tests pass. Behavior is unchanged.

## Criteria
- **No speculative features.** Build only what the task needs. No options or hooks for possible future use.
- **No overengineering.** Use the simplest solution that works. No extra layers or patterns.
- **No needless abstraction.** No single-use or pass-through wrappers. No interfaces that have one implementation.
- **No duplication.** Each piece of logic or value lives in one place. Reuse existing helpers and libraries.
- **No dead code.** Delete unused code, imports, files, dependencies and commented-out code.
- **No weak tests.** Each test checks real behavior and fails when that behavior breaks. No duplicate tests or mock-only tests.
- **No deep nesting.** Return early. Split long functions.
- **No vague names.** Names say what a thing holds or does. Avoid `x`, `data` and `helper`.
- **No magic values.** Give unexplained numbers and strings a named constant.
- **No useless comments.** Comments explain why. Delete comments that restate the code.
