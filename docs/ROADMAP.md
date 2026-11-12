# Roadmap

## v1.0.0 — Released 11 Nov 2026
- Single-cycle robotic CNC simulation; robot/CNC coordination, watch-table fault testing and one-page WinCC Unified overview.

## v1.1 — Implemented and simulation-tested; source export/release checks pending
- Auto mode, production target, continuous run, target stopping, Stop After Cycle.
- Scheduled machining fault 106 on chosen attempt; controlled halt and rejected-part scrap recovery.
- Explicit restart of interrupted batch without re-counting good parts.
- Two WinCC Unified pages; live automatic batch progress and status.
- Final source export and archive review; dedicated HMI START event test remain.

## v1.2 — Reliability and operator command hardening (proposed)
- PLC acknowledged command requests; robust HMI START and STOP handshake and communications-quality handling.
- Clearly indicated Auto/Manual state and denied-action reasons; PLC-side permission interlocks.
- Better attempt numbering with failed attempts tracked separately; bounded retries and raw-part inventory.
- Additional robot execution/acceptance fault scenario regression tests.

## v2.0 — Robot HMI and simulated SCADA (proposed)
- Robot and CNC diagnostics, active job / robot status, door and chuck visualization.
- Alarm history, acknowledgments, trend archives, cycle time, production KPIs and appropriate operator roles.
- Physical machine-safety interface remains outside simulation scope.
