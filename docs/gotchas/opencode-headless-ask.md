---
title: OpenCode headless runs auto-approve "ask" permissions
kind: gotcha
applies_to: [all]
status: verified
owner: agent-platform
last_verified: 2026-10-29
tags: [opencode, permissions, ci, headless, security]
---
## Symptom
In a CI or other unattended run, an agent executed a command (e.g. `git push`) that the
config marked `"ask"`, and nobody approved it.

## Cause
`opencode run --auto` auto-approves every permission that isn't explicitly denied. In
unattended runs, `ask` effectively means `allow`. Source: OpenCode CLI docs, `run --auto`
("Auto-approve permissions that aren't explicitly denied").

## Fix
- Anything that must never happen unattended must be `"deny"`, not `"ask"`.
- agent-platform runs unattended work with `agent --headless <profile>`. That applies
  `core/opencode.headless.json`, which defaults bash to `deny` and denies `git commit` /
  `git push` (the dispatcher does git).
- `tools/check.py` fails if a headless render has bash `"*"` set to anything but `deny`.
- The real limit is still GitLab: protected `main` and a Developer-role token per profile.

## How confirmed
Checked against the OpenCode CLI documentation for `opencode run` on 2026-10-29.
