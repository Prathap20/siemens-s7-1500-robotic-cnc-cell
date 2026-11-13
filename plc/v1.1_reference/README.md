# v1.1 implementation reference — NOT FINAL TIA EXPORT

- `FB_CellController_v1.1_AutoProduction_BODY.txt`: prepared automatic-production implementation body used during development.
- `FB_CellController_v1.1_FaultDemo_BODY.txt`: prepared fault demo implementation body that adds selected-attempt scheduling/resume logic to auto production.
- `FB_CellController_v1.1_FaultDemo_changes.diff`: differences relative to prepared AutoProduction body.
- `DB_FaultDemo.scl`: proposed declaration for the four-field deterministic simulation DB.

Screenshots of PLCSIM tests show working logic consistent with the designed behavior. These reference files do **not** establish exact byte-for-byte identity with the latest compiled v1.1 controller, and do not contain a complete combined generated source with updated static fields and DBs. Use the actual final TIA source export in `../exported/` for the public authoritative code release.
