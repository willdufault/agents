---
name: git-commit
description: Use when committing changes to git or drafting a commit message.
---

```
<type>: <one-line description>

<optional context>

Co-authored-by: <agent name> <agent email>
```

- Types: build, chore, ci, docs, feat, fix, perf, refactor, revert, style, test. No scopes.
- Breaking change: add `!` after the type (`feat!:`) and explain the break in the body.
- Keep the title at 50 columns or fewer.
- Wrap body lines at 72 columns.
- Split large changes into one thing per commit.
- Tests pass at every commit.
- Commit only. Never push.
- Footer: only the `Co-authored-by` line. No session link.
