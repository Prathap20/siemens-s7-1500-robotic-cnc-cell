# PLC external source export audit — v1.0

**Included file:** [`PLC_CNC_Cell_Full_Source_Export.scl`](../plc/exported/PLC_CNC_Cell_Full_Source_Export.scl)

- File size: **54,990 bytes**
- SHA-256: `c45b9cee1e1c4727afcccb64e1b7068802b4266ed2b9080171222691b0a21456`
- Parsed declaration count: **five FUNCTION_BLOCK, twelve DATA_BLOCK and four TYPE** declarations.
- FBs: `FB_CellController`, `FB_CNCController`, `FB_CNCSimulator`, `FB_RobotInterface`, `FB_RobotSimulator`.
- The original root-level `PLC_CNC_Cell.scl` contained 15 declarations. Those 15 matched the corresponding declarations in the full source export exactly; the full source additionally contains six DBs. The root-level file was excluded to avoid duplicating definitions.
- `Main [OB1]` is graphical and is **not** exported in this `.scl`; see [OB1 overview](../assets/Robotic_CNC_Cell_OB1_All_Networks.png).
- The green `FC_RobotI...` shown in [Program blocks overview](../assets/plc_program_blocks_overview.png) was not exported; its definition and use should be inspected in the `.zap21` before claiming complete independent PLC source-level reproduction.
- This is a structural source review, **not** a TIA Portal source compilation, a full project restore or confirmation that the `.scl` bytes match the simulated PLC download. Only Siemens TIA Portal can validate those steps.

The original engineering archive is retained separately and is not included in the public source ZIP, pending user-configuration and licensing review.
