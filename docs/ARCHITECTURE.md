# Architecture and signal ownership

## PLC components

1. `FB_CellController`: supervisory machine states, coordinates robot and CNC, count good and rejected parts, monitors fault codes and recovery states.
2. `FB_RobotInterface`: generates robot request / sequence ID handshake, watchdogs and reset.
3. `FB_RobotSimulator`: models job acceptance, execution, completion, faults and status.
4. `FB_CNCController`: orchestrates door/chuck/machining cycle and workpiece load/unload confirmations; includes CNC scrap recovery 950–959.
5. `FB_CNCSimulator`: models virtual CNC state, statuses, timed motion and machining, interlocks and injected machining fault 106.

Observed OB1 order from earlier engineering screenshot: Cell Controller, Robot Interface, Robot Simulator, CNC Controller, CNC Simulator. Verify the final archived project remains identical.

## Robot data flow

`DB_RobotTest` is the supervisor ↔ interface test I/O. `DB_RobotIO.Command` is written by the robot interface, and `DB_RobotIO.Status` by robot simulator. Relevant job IDs: 10 LOAD, 20 UNLOAD, 30 MOVE HOME.

## CNC data flow

`DB_CNCTest` carries supervisory StartCycle, LoadComplete, UnloadComplete, Reset, Abort and scrap recovery commands. `DB_CNCIO.Command` contains simulated door/chuck/start/load/unload requests; `DB_CNCIO.Status` contains actuator and process statuses.

`DB_CNCIO.Command.RobotClear` is **manually set** to TRUE in the watch table for v1.0. This is an educational operational permissive, NOT a safety function. No automatic cell-level RobotClear logic is claimed.

## Fault and recovery signal paths

- Robot error 201/203 from `FB_RobotInterface` causes supervisor cell fault 401.
- CNC simulator error 106 -> CNC controller fault 300 -> supervisor fault 402.
- Machining-fault recovery: supervisor 960–967 coordinates CNC recovery 950–959, robot unload job 20, and increments RejectedParts once, not PartsCompleted.
- Finished part after robot unload interruption: recovery supervisor 920–940; increment good count only after confirmed unload completion.

## Important design constraints

- Single-writer ownership of commands must be maintained.
- Watchdogs must run every PLC scan as specified.
- Fault reset and restart must depend on physical/simulated workpiece state rather than just clearing a status bit.
- This is non-safety-rated simulation software; no claim of real machinery compliance.


## v1.1 extension — automatic batching and fault demonstration

`FB_CellController` owns production mode, target, automatic repetition and stop-after-cycle state. It records a batch-good baseline, latches a target at accepted START and uses a wait-for-ready transition before repeating. Stop After Cycle requests completion of the current in-flight cycle before new work is issued.

For demonstration only, `DB_FaultDemo.Enable`, `TriggerAttempt`, `CurrentAttempt` and `Triggered` select one machining attempt. The controller sets `DB_SimControl` fault bits when the CNC is machining; CNC fault 106 propagates to cell error 402, halting automatic repeat. After operator Reset and scrap unload via pre-existing recovery states 960–967, a **new** Start resumes the incomplete original good-part target. This is not unattended fault reset.

The operator screen `02_Automatic_Production` connects to `DB_CellTest.AutoMode`, `.StopAfterCycle`, `.TargetGoodParts`, `.AutoRunning`, `.BatchGoodParts` and `.TargetReached`. The original `01_Production_Overview` remains available. The HMI has 16 tags total.

The **final v1.1 external source is not bundled** here; implementation reference files reside in `plc/v1.1_reference/` and must be superseded by an actual TIA Portal final export. `RobotClear` remains a manual simulation permissive.
