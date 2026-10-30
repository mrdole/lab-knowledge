---
title: Internal GitLab instance - version and available features
kind: reference
applies_to: [all]
status: draft
owner: CHANGEME
tags: [gitlab, version, mcp, kas, kubernetes, api]
---
## Facts
| Item | Value |
|------|-------|
| Version | 18.11.7-ee |
| GitLab MCP server (`/api/v4/mcp`) | Not available. Agents use `glab` and the REST API instead. |
| KAS (GitLab agent for Kubernetes) | Enabled |
| License tier | CHANGEME (affects MR approval rules such as "prevent approval by author") |

## What this means for agents
- GitLab access is `glab` plus the REST API, using the profile's project access token (bot identity).
- Don't configure a GitLab MCP server in any profile. Revisit after an upgrade to 19.5+
  (GA there; its read toolsets could then serve interactive sessions).
- Everything in agent-platform (project access tokens, token rotation, protected branches, CI
  variables, labels, dispatcher) works on 18.11.

## How confirmed
Version and MCP availability reported by the user on 2026-10-30. Verify the version with
`curl -s https://<gitlab-host>/api/v4/version` before marking this verified.
