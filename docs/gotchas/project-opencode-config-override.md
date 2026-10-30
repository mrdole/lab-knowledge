---
title: A repo's own opencode.json overrides the agent profile
kind: gotcha
applies_to: [all]
status: verified
owner: agent-platform
last_verified: 2026-10-29
tags: [opencode, config, permissions, dispatcher]
---
## Symptom
An agent working in a particular repo ignores profile permissions or uses a different
model or agents than the profile defines.

## Cause
OpenCode merges config sources. A project's `opencode.json` and `.opencode/` directory
load **after** the custom config passed in `OPENCODE_CONFIG` (which is how the `agent`
launcher passes the profile), so the project's settings win for conflicting keys.

## Fix
- Project repos carry only `AGENTS.md` (facts and commands) and, if needed,
  `.agents/skills/`. They don't carry their own OpenCode config.
- The dispatcher refuses repos that contain `opencode.json`, `opencode.jsonc` or
  `.opencode/` and labels the issue `agent::needs-human`.
- If a repo genuinely needs different permissions, make that a platform profile.

## How confirmed
Checked against the OpenCode config documentation (precedence order) on 2026-10-29.
