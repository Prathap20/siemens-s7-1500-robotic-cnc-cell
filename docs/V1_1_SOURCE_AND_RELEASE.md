# v1.1 source provenance, release readiness and GitHub push steps

## Read this before pushing

The repo contains the **published v1.0 combined SCL export under `plc/baseline_v1.0`** and the **v1.1 development body/diff under `plc/v1.1_reference`**. This is intentional. The complete **final** v1.1 exported SCL source is **not currently included**.

To finish the code release in TIA Portal V21:

1. Open and save the tested `Robotic_CNC_Cell_v1.1` project; confirm `FB_CellController` includes AutoMode, StopAfterCycle, TargetGoodParts, AutoRunning, BatchGoodParts, TargetReached and static ResumePending.
2. Export external SCL source from all current SCL blocks, UDTs and global DBs **including `DB_FaultDemo` and updated `DB_CellTest`**. In TIA, use *Generate source from blocks → Including dependent blocks* as appropriate, verify file names and actual contents.
3. Name the final exported file `plc/exported/PLC_CNC_Cell_v1.1_Final_Source_Export.scl`. Its contents must be generated from *the final saved TIA project*, not copied from the v1.0 source file.
4. Archive the current engineering project to `Robotic_CNC_Cell_v1.1_Final.zap21` outside the public repo; retain a private backup. Review user-management configuration, project backups and secrets before any public archive distribution.
5. Compile PLC/HMI from the final project and save the reports. Review the remaining HMI START button event and two-screen navigation before calling the public release fully validated.

## How to update your existing GitHub Desktop repository

- Check out the `v1.1-development` branch first. **Do not create a new repository** or initialize another nested `.git` folder.
- Extract this release package and **copy its contents** (not the outer folder) into the existing local repository root. Keep the existing hidden `.git` directory untouched.
- This package relocates the old `plc/exported/PLC_CNC_Cell_Full_Source_Export.scl` into `plc/baseline_v1.0/`. GitHub Desktop may show a deletion of the old path and an addition at the new path. This is intentional.
- Add your authoritative new v1.1 export to `plc/exported/` once available.
- Review the Changes tab: confirm screenshots, source provenance and docs, and no `.zap21`/user-management or other sensitive backup files. Commit to `v1.1-development` and click Push origin.
- Open a pull request to `main` only when ready; publish official `v1.1.0` after final source export and outstanding tests are verified.

Suggested commit summary: `Document v1.1 automatic production, fault recovery and two-screen HMI`

## Expected missing items until final TIA export

- Final generated v1.1 PLC SCL/UDT/DB import source
- Final updated `.zap21` archive (intentionally private)
- Separate HMI START command test screenshot/trace
- Dedicated final PLC Stop After Cycle watch-table screenshot
