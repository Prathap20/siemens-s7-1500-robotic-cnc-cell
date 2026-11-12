# Changelog

## [Unreleased] — v1.1 development, 2026-11-12

### Added and tested in S7-PLCSIM Advanced
- Continuous production from a single START, configurable target, batch-good count and TargetReached indication (TC-AUTO-01).
- Operator Stop After Cycle — complete in-flight cycle and stop below target (TC-AUTO-02).
- Deterministic machining fault 106 on attempt 3 using DB_FaultDemo (TC-AUTO-03).
- Fault halt, operator-initiated scrap recovery and rejected-part accounting (TC-AUTO-04).
- Explicit restart to finish interrupted target after recovery (TC-AUTO-05).
- Second WinCC Unified screen with 16 HMI tags and verified 0-error / 0-warning compile.
- Live Auto Running and Target Reached HMI indicators; Stop After Cycle command observed in PLC.

### Outstanding release checks
- Export *actual final* v1.1 combined SCL/DB/UDT declarations and `.zap21` backup from TIA Portal.
- Confirm HMI START/target writing independent of PLC watch-table operations; test final STOP state and navigation if necessary.
- Verify no confidential runtime credentials in materials to be published; no physical safety validation.

## [1.0.0] — 2026-11-11
- Published v1.0 cell supervisor, robot/CNC simulation, state machines, handshakes, watch-table fault recovery and WinCC Unified one-cycle HMI monitoring.
- Live two separate normal HMI-started cycles, good-parts count 0 to 2, and return to Ready.
- Original external TIA SCL source export (five FBs, twelve DBs, four UDTs) retained in `plc/baseline_v1.0/` for historical reference.
