---
name: create-pr
description: Use when opening a pull request.
---

```
## Overview
<high-level changes>
[optional: ASCII art]

## Files touched
- `<path>`: <why>

## Validation
<steps taken, evidence>

## Risk
<N>/10 — <one-line reason>

🤖 Generated with <agent name>
```

- Title like commit: `<type>: <one-line description>`. No scope.
- Source: current branch.
- Destination: not main by default. Guess closest remote branch (fewest commits from merge-base to HEAD); confirm with user first.
- Then push and run `gh pr create`.
- Risk: cost of a mistake. 1 = confident, low risk; 10 = unsure, high risk.
