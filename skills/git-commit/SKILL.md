---
name: git-commit
description: Use when committing changes to git.
---

```
<type>: <one-line description>

<optional context>

Co-authored-by: <agent name> <noreply@anthropic.com>
```

- Type: build, chore, ci, docs, feat, fix, perf, refactor, revert, style, test. No scope.
- Split large changes; one thing per commit.
- Tests pass at every commit.
- Commit only; never push.
