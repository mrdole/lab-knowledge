---
title: Agent labels, tokens and protected branches in GitLab
kind: reference
applies_to: [all]
status: draft
owner: CHANGEME
tags: [gitlab, tokens, labels, dispatcher, protected-branches]
---
## Labels (per project)
`agent::ready` → `agent::running` → `agent::review` | `agent::needs-human` | `agent::failed`,
plus `profile::<name>` to choose the profile.

## Tokens
One bot token per profile, stored as a masked, protected CI/CD variable. Names, roles and
scopes are in `agent-platform/docs/security.md`. Record here which projects each token is
created in, and its expiry:

| Variable | Created in | Expires | Rotated by |
|----------|------------|---------|------------|
| GITLAB_TOKEN_FIRMWARE | CHANGEME | | |

## Protected branches
`main`: no direct pushes, approvals required, author can't approve. Note any project
that differs, and why.

## How confirmed
<fill in when verified>
