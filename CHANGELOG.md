# Changelog

## [1.0.0] — 2026-11-11 (prepared release candidate)

### Verified
- WinCC Unified HMI compiled with 0 errors and 0 warnings.
- Live PLC ↔ HMI interactions demonstrated: Ready and Busy indicators, HMI-initiated production, counter updates 0→1→2 and return to Ready.
- Earlier robotic handshake, CNC machining, fault injection and recovery tests documented.

### Limitations
- RobotClear is manual simulation input.
- HMI Reset has not been verified in a live fault recovery test.
- Automatic repeat and scheduled fault campaigns are reserved for v1.1.
- Authoritative project archive received and structurally validated. Combined external SCL export (5 FBs, 12 DBs, 4 UDTs) is included; graphical OB1 and additional FC are not included in SCL. Siemens restore and binary-archive public-distribution review remain pending.
