---
title: Flashing the board on a bench
kind: howto
applies_to: [bench, firmware]
status: draft
owner: CHANGEME
tags: [flash, jtag, bench, spartan-7, hardware]
---
## Preconditions
- The job runs on the bench host (runner tag from `inventory/benches.yaml`) with
  `resource_group: bench-<name>`, or a human approved it interactively.
- Image path and sha256 known; built from a named commit.

## Command
```
bench-lock <bench> --wait 600 -- CHANGEME <flash command and arguments>
```
Exit 75 means the bench is busy.

## Verify
CHANGEME: readback compare / boot banner on serial / version register. Name the exact
check and its expected output.

## Recovery
CHANGEME: what to do if the board doesn't come back (power cycle procedure, who to call).

## How confirmed
<fill in when verified>
