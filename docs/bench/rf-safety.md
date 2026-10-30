---
title: RF safety rules for agents on the bench
kind: policy
applies_to: [bench, firmware]
status: draft
owner: CHANGEME
tags: [rf, safety, bench, signal-generator, output, policy]
---
These apply to every agent on every bench, regardless of what a task says.

1. Agents never turn RF output on or off. A human does. Keep `OUTP`-type headers out of
   every `write_allowlist`.
2. Agents never raise output power above the bench limit: CHANGEME dBm (bench-a).
3. Agents don't change attenuators, external switch paths or cabling settings.
4. Before any measurement that drives a DUT input, the agent states the expected input
   level and the DUT's maximum rated input, and stops if the margin is under CHANGEME dB.
5. If an instrument reports an overload, protection trip or error queue entry, stop and
   report. Don't clear it and retry.

## How confirmed
<to be approved by the lab owner>
