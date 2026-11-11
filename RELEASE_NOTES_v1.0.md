# v1.0.0 — Robotic CNC Machine Tending Cell

**Summary:** Siemens S7-1500 SCL state-machine orchestration of a simulated robot and CNC machine with WinCC Unified browser HMI.

### Included
- Sequenced robot job handshake with watchdogs
- Virtual CNC door, chuck, workpiece and machining states
- Fault detection and targeted recovery paths, including rejected workpiece accounting
- Operator Start and Reset controls plus live Ready/Busy/Fault indicators
- Demonstrated two successful HMI-initiated production cycles (Good Parts 0→1→2)

### Test environment
TIA Portal V21; simulated CPU 1516-3 PN/DP; PLCSIM Advanced V8 Update 1; WinCC Unified PC Runtime.

### Known limitations
- Simulation only; not safety rated; no physical equipment.
- RobotClear manually asserted in test watch table.
- HMI Reset not yet tested end-to-end; continuous Auto mode not yet included.
- A final `.zap21` was supplied and passed ZIP integrity validation but is distributed separately pending privacy/licensing review. A combined external SCL export (5 FBs, 12 DBs, 4 UDTs) is provided; independent Siemens restore/compile validation remains pending. Graphical OB1 and an additional FC require the TIA archive.

### Next version
v1.1 will add continuous mode, production target, Stop after cycle, and deterministic fault scenarios with bounded recovery.
