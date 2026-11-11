# Development roadmap

## v1.0 — Baseline (tested)

- PLC robot/CNC sequence and interlocks
- Robot job handshake / sequence IDs / watchdogs
- CNC machining fault 106 injection and scrap recovery
- Finished-part unloading recovery
- Browser-based HMI with Start/Reset, KPIs and Ready/Busy/Fault status
- Two consecutive HMI-initiated completed parts verified
- Manual RobotClear permissive documented

## v1.1 — Batch automation and controlled faults (planned)

- Add explicit auto/manual mode, target parts, stop-after-cycle, raw-parts inventory
- Supervisor owns the repeated Start pulse only after clean idle, accepted recovery and appropriate machine conditions
- Add deterministic one-shot fault scenario manager (scheduled by cycle index and phase)
- Reuse: DisableJobAcceptance; FreezeRobotExecution; RejectUnloadJob; InjectMachiningFault
- Fault requires correct stop, retained workpiece state and appropriate operator acknowledgement; do not auto-clear unsafe or unresolved alarms
- Bounded retry policy; verify no double counting; distinguish finished parts, scrap and unfinished attempts
- Automatic fault scenario tests and real HMI reset/recovery verification
- Ensure command ownership: avoid multiple writers to DB_RobotTest/DB_CNCTest/DB_SimControl signals

## v2.0 — Industrial HMI and simulated SCADA (planned)

- Robot HMI: Ready, Busy, AtHome, AtSafePosition, gripper, active JobID, SequenceID, FaultCode
- CNC HMI: DoorOpen, DoorClosed, ChuckClamped, PartPresent, CycleRunning, CycleComplete
- Alarm banner, history, priority, acknowledgement and tag quality
- Cycle time, throughput, trends, production target attainment, rejects
- Appropriate user permissions, screen navigation, supervised manual functions
- Optional SCADA archive/reporting dependent on WinCC Unified license/runtime environment

Safety note: any future motion permissive derived from robot status is still simulation-only and must never be represented as a safety-rated clearance mechanism.
