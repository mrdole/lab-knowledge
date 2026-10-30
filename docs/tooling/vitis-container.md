---
title: vitis-dev build container (Vitis 2024.2, Spartan-7)
kind: reference
applies_to: [firmware, pipeline]
status: draft
owner: CHANGEME
tags: [vitis, vivado, xilinx, container, podman, build, spartan-7, xsa]
---
## Image
- Name and tag: `CHANGEME/vitis-dev:2024.2-<n>`
- Built from: the `vitis-dev` repo (Dockerfile). Tested locally with Podman first.

## Inputs
- The build starts from an **XSA/bitstream exported elsewhere**. Builds here never
  synthesize from RTL.
- Where the XSA comes from: CHANGEME (artifact path / package registry).

## Running a build
```
podman run --rm -v "$PWD":/work:Z -w /work CHANGEME/vitis-dev:2024.2-<n> <build command from the repo's AGENTS.md>
```
- License settings, if any: CHANGEME (name the variable; never the license server secret).
- Extra mounts: CHANGEME

## Known failures
| Symptom | Cause | Fix |
|---------|-------|-----|
| CHANGEME | | |

## How confirmed
<fill in when verified>
