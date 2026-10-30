---
title: Trusting the corporate CA on RHEL (system, Node/OpenCode, Python, pip)
kind: howto
applies_to: [all]
status: draft
owner: CHANGEME
tags: [tls, ca, certificates, rhel, node, python, opencode]
---
## System trust (RHEL 9)
1. Copy the PEM certificate(s) to `/etc/pki/ca-trust/source/anchors/`.
2. Run `sudo update-ca-trust`.
3. Check: `openssl s_client -connect <host>:443 -servername <host> </dev/null` shows
   `Verify return code: 0 (ok)`.

## Tools that don't use the system store by default
- **Node (OpenCode):** `NODE_EXTRA_CA_CERTS=/etc/pki/tls/certs/ca-bundle.crt`
  (site.env sets this).
- **Python requests:** `REQUESTS_CA_BUNDLE=/etc/pki/tls/certs/ca-bundle.crt`
  (site.env sets this).
- **pip:** `pip config set global.cert /etc/pki/tls/certs/ca-bundle.crt`, or set the same
  environment variable as for requests.
- **Containers:** the image has its own trust store. Put certs in
  `agent-platform/core/certs/` before building.

## Which certificates
CHANGEME: name the CA files and where to get them.

## How confirmed
<fill in when verified>
