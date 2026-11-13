> **Historical v1.0 baseline document.** For the v1.1 test results and current code provenance see [v1.1 validation](V1_1_VALIDATION.md) and [source/release checklist](V1_1_SOURCE_AND_RELEASE.md).

# Validation matrix — v1.0 baseline

**Evidence source:** operator screenshots and earlier watch-table observations during TIA Portal / S7-PLCSIM Advanced simulation. These are functional simulation observations, not hardware acceptance testing.

| ID | Test | Evidence | Result / scope |
|---|---|---|---|
| HMI-00 | WinCC Unified PC engineering compile | `assets/hmi_compile_success.png` | PASS: 0 errors, 0 warnings |
| HMI-01 | Click START CYCLE | `assets/hmi_01_busy.png` | PASS: HMI BUSY amber, READY grey |
| HMI-02 | Finish one CNC cell production cycle | `assets/hmi_02_first_good_part.png` | PASS: Good Parts 1; Ready green; ErrorCode 0 |
| HMI-03 | Finish another production cycle | `assets/hmi_03_second_good_part.png` | PASS: Good Parts 2; Ready green; ErrorCode 0 |
| HMI-04 | PLC / HMI readiness indication | `assets/plc_watch_table_ready.png`, `assets/hmi_04_ready_before_start.png` | PASS: PLC Ready TRUE and HMI READY green with manual RobotClear TRUE |
| CELL-03 | Robot execution watchdog | Earlier PLC watch-table captures in conversation | PASS: interface error 203 propagates as Cell 401; reset recovery observed |
| CELL-05 | Robot unload job rejection | Earlier PLC watch-table captures in conversation | PASS: rejection fault propagation and manual reset/recovery observed |
| CELL-04 | CNC machining fault 106 | Earlier PLC watch-table captures in conversation | PASS: CNC FaultCode 106, CNC fault 300, Cell 402 |
| CELL-04R | Recover faulty machined part as scrap | Earlier watch-table captures in conversation | PASS: rejected count 1, completed count 0, controller returned Ready |
| HMI-05 | Live HMI Reset action during fault | Not yet captured | NOT VERIFIED |
| AUTO-01 | Unattended continuous batch production | Not in v1.0 | NOT IMPLEMENTED |
| AUTO-FAULT | Scenario-driven multi-cycle fault campaign | Not in v1.0 | NOT IMPLEMENTED |

## Acceptance criteria for v1.0

- HMI can initiate a normal cycle and show its status changes.
- At least two sequential normal production cycles are demonstrated via HMI.
- Good-parts count increments exactly once per completed cycle.
- Robot/CNC standalone fault-recovery test evidence is preserved.
- The project is identified as simulation-only, with manual RobotClear and other limitations documented.

## Important verification needed before declaring a fully reproducible release

A combined SCL export with five FBs, twelve DBs and four UDTs is included. Independent consistency with the TIA Portal runtime and a full restored/compiled Siemens project has not been verified; review the separate `.zap21` archive when available. Also note that graphical OB1 and an additional FC are not exported. The historical snapshots under `plc/reference_snapshots/` can differ from the final online code and omit block interfaces; they are provided only as review context.
