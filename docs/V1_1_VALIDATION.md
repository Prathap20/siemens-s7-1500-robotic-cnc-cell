# v1.1 Validation Matrix — PLCSIM Advanced and WinCC Unified

Evidence is based on screenshots from 11–12 November 2026. All observations are from **simulated** PLC/robot/CNC, not production machinery. A static final screenshot cannot prove every transient state; rows distinguish final evidence from the interpreted scenario.

| ID | Test / criterion | Screenshot evidence | Result |
|---|---|---|---|
| TC-AUTO-01 | Automatic batch target 3 | [`TC_AUTO_01_ThreePartTarget.png`](../assets/v1.1/TC_AUTO_01_ThreePartTarget.png) | PASS: BatchGoodParts=3, TargetReached=TRUE, AutoRunning=FALSE, Ready=TRUE, ErrorCode=0 |
| TC-AUTO-02 | Stop After Cycle with target 10 | [`TC_AUTO_02_StopAfterCycle_PLC.png`](../assets/v1.1/TC_AUTO_02_StopAfterCycle_PLC.png) | PASS / final state: BatchGoodParts=5, StopAfterCycle=TRUE, TargetReached=FALSE, AutoRunning=FALSE, Ready=TRUE, ErrorCode=0 |
| TC-AUTO-03 | Fault injection on attempt 3 | [`TC_AUTO_03_MachiningFault106.png`](../assets/v1.1/TC_AUTO_03_MachiningFault106.png) | PASS: Triggered=TRUE, CurrentAttempt=3, BatchGoodParts=2, CNC FaultCode=106, Cell ErrorCode=402, StateOut=900, auto stopped, injection bits false |
| TC-AUTO-04 | Scrap recovery | [`TC_AUTO_04_ScrapRecovery.png`](../assets/v1.1/TC_AUTO_04_ScrapRecovery.png) | PASS / final state: RejectedParts increment 0→1, BatchGoodParts remains 2, cell state 0/Ready, CNC part absent |
| TC-AUTO-05 | Explicit resume interrupted batch | [`TC_AUTO_05_ResumeBatch.png`](../assets/v1.1/TC_AUTO_05_ResumeBatch.png) | PASS: BatchGoodParts=3, RejectedParts=1, TargetReached=TRUE, Ready=TRUE, ErrorCode=0; CurrentAttempt=4 is next-attempt diagnostic, not a fourth completed part |
| TC-HMI-00 | HMI compilation | [`HMI_02_Compile_ZeroErrors.png`](../assets/v1.1/HMI_02_Compile_ZeroErrors.png) | PASS: 16 configured tags, 2 screens, 1 connection, 0 errors, 0 warnings |
| TC-HMI-01 | Automatic Production live feedback | [initial](../assets/v1.1/HMI_02_Initial.png), [running](../assets/v1.1/HMI_02_AutoRunning.png), [completed](../assets/v1.1/HMI_02_TargetReached.png) | PASS: Target 2; BatchGoodParts 0→1→2; Auto Running amber while running, Target Reached green after completion; PLC-to-HMI update verified |
| TC-HMI-02 | HMI Stop After Cycle | [PLC stop tag](../assets/v1.1/HMI_02_StopRequest_PLC.png), [Runtime stopped](../assets/v1.1/HMI_02_StopAfterCycle_Result.png) | PASS with evidence qualification: StopAfterCycle TRUE while PLC running; Runtime later Auto Running inactive with batch below target. Dedicated final PLC watch-table state not captured. |
| TC-HMI-03 | HMI START command specifically | No isolated event/edge trace | **NOT FULLY VERIFIED**: after earlier attempts the successful production start was issued from PLC watch table; a separate HMI-only start validation is required. |
| TC-HMI-04 | Navigation between screens | Second screen visible, back button installed | **PARTIAL**: screen rendered, but two-way navigation not separately captured. |
| TC-RELEASE-01 | Restore/compile final v1.1 archive | Not supplied | **NOT VERIFIED** |

## Invariants observed
- CNC machining failure increments rejected count only after scrap recovery; good-part batch count stayed at 2 until a later, separately successful run.
- Fault injection bits were false while fault 106 remained latched; operator RESET was used for recovery.
- Target-reached logic prevented further repetition on the documented 3-good-part batch.
- `RobotClear` was manually TRUE for all test runs; it remains a simulated permissive, not a safety signal.

## Remaining risks
- The currently provided final v1.1 implementation is available only as prepared code bodies and chat evidence; exact engineering source export is needed for reproducibility.
- HMI START Press/Release may require a more robust command acknowledgment for production-grade use.
- No real hardware, emergency-stop, safe-stop or protective interlock certification exists.
