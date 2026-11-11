# Authoritative TIA Portal external source export

`PLC_CNC_Cell_Full_Source_Export.scl` contains the source for **five PLC function blocks, twelve data blocks and four user-defined data types**. It was generated from the working TIA V21 project. Use a TIA Portal V21 environment to import/compile; the file alone does not reproduce the complete engineering project.

This file is a **single combined import source**. Do not import an additional export containing the same FB/UDT/DB declarations without checking for duplicates.

For graphical Main [OB1] calls use the original stitched screenshot in `assets/Robotic_CNC_Cell_OB1_All_Networks.png`; the complete OB1 resides in the separately held `.zap21` project archive. An additional function shown in the Program blocks UI (`FC_RobotI...`) is not included in the SCL export.

See [Source export audit](../../docs/SOURCE_EXPORT_AUDIT.md) for exact coverage and limitations.
