---
title: RHEL on WSL for agent work (networking, file locations)
kind: howto
applies_to: [all]
status: draft
owner: CHANGEME
tags: [wsl, rhel, networking, vpn, performance]
---
## Networking
- With the corporate VPN/proxy, mirrored networking usually behaves better than NAT.
  Put this in `%UserProfile%\.wslconfig`:
  ```
  [wsl2]
  networkingMode=mirrored
  ```
  Then `wsl --shutdown` and reopen.

## Files
- Keep repos in the Linux filesystem (`~/repos`), not under `/mnt/c`. Agents read many
  files, and cross-filesystem access is much slower.
- `lab-knowledge` lives at `~/repos/lab-knowledge` (`AP_KNOWLEDGE_ROOT`).

## Subscription
- Register with the company's activation key or Satellite, not a personal account:
  `sudo subscription-manager register --org=<ORG_ID> --activationkey=<KEY>`

## How confirmed
<fill in when verified>
