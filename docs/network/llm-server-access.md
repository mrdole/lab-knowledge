---
title: Reaching the internal LLM server (base URL, proxy, CA)
kind: reference
applies_to: [all]
status: draft
owner: CHANGEME
tags: [network, proxy, llm, tls, opencode]
---
## Endpoint
- Base URL (OpenAI-compatible): `CHANGEME` (agents get it as `AP_LLM_BASE_URL`)
- List models: `curl -s -H "Authorization: Bearer $CORP_LLM_KEY" "$AP_LLM_BASE_URL/models"`
- Auth: bearer key in `CORP_LLM_KEY` (from `secrets.env` or a CI variable). Never in a doc.

## From which networks
- Workstations (WSL): CHANGEME. Does it need the proxy, or is it in `NO_PROXY`?
- Agent servers: CHANGEME
- Lab/bench subnet: CHANGEME

## Common failures
| Symptom | Likely cause | Check |
|---------|--------------|-------|
| `self signed certificate in certificate chain` / `UNABLE_TO_GET_ISSUER_CERT_LOCALLY` from OpenCode | Node doesn't use the system CA store | `NODE_EXTRA_CA_CERTS` set? See `tooling/rhel-corp-ca.md` |
| Timeout from WSL but works from Windows | WSL NAT networking / VPN | `.wslconfig` `networkingMode=mirrored`; see `tooling/wsl-rhel.md` |
| 407 / proxy errors | LLM host not in `NO_PROXY` | `env | grep -i proxy` (don't paste secrets) |
| Model not found | Model ID differs from `core/opencode.core.json` | compare with `/models` output |
| `apiKey` shows `***` in `opencode debug config` | Normal: OpenCode redacts keys in debug output | not a problem |

## How confirmed
<fill in when verified>
