# Restore and reproduce v1.0

## Requirements

- TIA Portal V21 with S7-1500 support
- S7-PLCSIM Advanced V8 Update 1 (compatible simulated CPU)
- WinCC Unified PC Runtime and working HMI-to-PLC communications for full HMI demonstration
- TIA archive `Robotic_CNC_Cell_HMI_Implementation.zap21` (held privately by the author; not included)

## Import

1. Open **TIA Portal V21 → Project → Retrieve** and select the `.zap21` archive.
2. Verify the S7-1500 CPU 1516-3 PN/DP and configured WinCC Unified PC Runtime device.
3. Compile the PLC and HMI. In the previously tested environment the HMI compiled with 0 errors/0 warnings.
4. Start S7-PLCSIM Advanced instance `CNC_Cell_Sim` (CPU S7-1500), download the PLC, switch it to RUN.
5. Open the cell watch table; confirm `DB_RobotTest.ReadyForJob`, `DB_CNCTest.Ready`, `DB_CNCIO.Status.MachineReady` TRUE and no active faults.
6. **Simulation-only manual permissive:** set `DB_CNCIO.Command.RobotClear := TRUE` via watch table. Verify `DB_CellTest.Ready := TRUE` (do not force the Ready output itself).
7. Start the WinCC Unified HMI simulation and verify its tag quality and READY lamp. The network path used in one cloud demonstration was PLC `192.168.0.1` / PC IE General `192.168.0.2` on PN/IE_1; **do not apply those settings blindly on another machine**.
8. Click START CYCLE once. Observe BUSY, then returned READY and one increment of Good Parts.
9. Capture HMI and watch-table evidence before modifying any PLC logic.

## Included source and future re-exports

A combined generated source `plc/exported/PLC_CNC_Cell_Full_Source_Export.scl` is included (5 FBs, 12 DBs, 4 UDTs). The graphical OB1 and an additional FC are absent from that source; restore the full project from the Siemens archive to inspect them.

If changing the PLC logic in future, generate a new external source from the tested project, and compare/export it before committing.


Right-click SCL blocks/PLC data types → **Generate source from blocks → Selected blocks only** or **Including dependent blocks**, and save `.scl`/`.udt`/`.db` as applicable. Export at least `FB_CellController`, `FB_RobotInterface`, `FB_RobotSimulator`, `FB_CNCController`, `FB_CNCSimulator`, and the associated DBs/UDTs. Check for exported secrets or internal IP information before publication. See official Siemens documentation: https://docs.tia.siemens.cloud/r/en-us/v21/creating-and-managing-blocks/using-external-source-files-for-stl-and-scl/saving-blocks-as-external-source-files

Archive: **Project → Archive → Archive as compressed file** → `.zap21`. Save first. Official reference: https://docs.tia.siemens.cloud/r/en-us/v21/editing-projects/archiving-and-retrieving-projects/creating-a-project-archive

## If the HMI shows tag-quality warning icons

Check CPU RUN, online watch table values, actual Runtime status, S7 connection mapping, and networking of the simulation. The engineering PN/IE_1 connection alone does not prove that the Runtime host and simulated CPU can communicate in a different environment.

## HMI command caveat

START/RESET presently use WinCC Unified Press => 1 and Release => 0 actions. This is adequate for a controlled simulated demo but should be replaced or augmented with PLC-controlled command acknowledgement, connection-loss behavior and permissions before production use.
