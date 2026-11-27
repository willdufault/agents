---
name: create-pr
description: Use when creating or drafting a pull request.
---

## Steps

1. `git remote get-url origin` → GitHub, Bitbucket, or CodeCommit.
2. Source: current branch.
3. Destination: not main by default. Guess closest remote branch (fewest commits from merge-base to HEAD); confirm with user first.
4. Scope: `git fetch`, then only the net diff `git diff origin/<dest>...HEAD`.
5. Title like commit: `<type>: <one-line description>`, no scope.
6. Evidence (if any): commit screenshots and GIFs to `pr-evidence` under `pr-<short HEAD hash>/`; keep only the 10 most recently committed folders. Link with the host URL below.
7. Push source, then run the host section below.
8. Send the PR link to the user.

## PR template

```
## Overview
- <area>: <what changed>

## Validation
<steps taken>

## Evidence
[optional: screenshots, GIFs]

## Confidence
<N>/5 — <one-line reason>

## Risk
<N>/5 — <one-line reason>

## Rollback
[only if Risk > 3]
1. <step>

🤖 Generated with <agent name>
```

- Overview: every change in the net diff, high level; no implementation details.
- Confidence: likelihood the changes have no bugs. 1 = likely buggy; 5 = certain bug-free.
- Risk: cost of a mistake. 1 = negligible; 5 = severe (outage or data loss).
- Rollback: numbered steps; only if Risk > 3.
- Footer: "🤖 Generated with" line only. No session link.

## GitHub

```
gh pr create --base <dest> --head <source> --title "<title>" --body "<desc>"
```

PR URL: `<URL from output>`
Evidence URL: `https://raw.githubusercontent.com/<owner>/<repo>/pr-evidence/pr-<hash>/<file>`

## Bitbucket

Build link (URL-encode title/description):

```
https://bitbucket.org/<workspace>/<repo>/pull-requests/new?source=<source>&dest=<dest>&title=<title>&description=<desc>
```

Also print title/description as plain text in case prefill is ignored.

PR URL (after creation): `https://bitbucket.org/<workspace>/<repo>/pull-requests/<id>`
Evidence URL: `https://bitbucket.org/<workspace>/<repo>/raw/pr-evidence/pr-<hash>/<file>`

## CodeCommit

```
aws codecommit create-pull-request --title "<title>" --description "<desc>" --targets repositoryName=<repo>,sourceReference=<source>,destinationReference=<dest>
```

PR URL: `https://<region>.console.aws.amazon.com/codesuite/codecommit/repositories/<repo>/pull-requests/<id>?region=<region>` (id from output)
Evidence URL: `https://<region>.console.aws.amazon.com/codesuite/codecommit/repositories/<repo>/browse/refs/heads/pr-evidence/--/pr-<hash>/<file>?region=<region>`
