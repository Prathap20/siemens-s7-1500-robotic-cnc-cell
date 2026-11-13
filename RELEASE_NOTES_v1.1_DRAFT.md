# Robotic CNC Machine Tending Cell — v1.1 (DRAFT)

**Do not publish as an official `v1.1.0` release until the final tested v1.1 source export and project archive have been saved, and pending HMI checks are reviewed.**

## Highlights
- Production-target automatic cycle repetition with one START command.
- Controlled Stop After Cycle command.
- Deterministic simulated CNC machining fault 106 at a selected attempt.
- Cell fault 402 detection, automatic-run halt and operator-initiated rejected-part unloading.
- Preserved good/rejected accounting and explicit restart of an interrupted batch.
- New WinCC Unified **Automatic Production** screen alongside the original **Production Overview**.

## Simulation evidence
- TC-AUTO-01 through TC-AUTO-05 passed in operator-provided watch-table screenshots.
- WinCC Unified compiled with **0 errors, 0 warnings**, **16 HMI tags**, **2 screens**.
- Runtime shows batch 0 → 1 → 2, Auto Running active/inactive, and Target Reached true at target 2.
- HMI Stop After Cycle asserted the PLC tag; stopped Runtime screen shows batch below target.

## Known limitations
- Simulation only; no safety-rated hardware or emergency-stop certification.
- Manual `RobotClear` permissive; engineering-only fault schedule configuration.
- The final v1.1 complete TIA source export and `.zap21` are not included in this prepared GitHub package.
- Direct HMI START event and all operator permissions have not been independently verified against a dedicated command trace.

## Recommended release artifacts
- Final exported SCL code / UDTs / DBs (from the saved, tested v1.1 TIA project)
- Two HMI screen screenshots and the test matrix
- Reviewed final engineering project archive attached as Release asset only if cleared for sharing
