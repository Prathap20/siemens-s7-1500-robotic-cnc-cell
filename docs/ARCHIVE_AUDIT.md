# Archive audit — Robotic CNC Cell v1.0

## Received file

- Filename: `Robotic_CNC_Cell_HMI_Implementation.zap21`
- Archive SHA-256: `44ef13b8c8aeb9c11bcc76e6b4d25d76a45b1b7bde87f1e8ef5ee73d2cb949c3`
- ZIP integrity test: **PASSED** (no corrupt members detected)
- ZIP file count: **2,950**
- Expanded member size: **89,035,123 bytes** (not disk space required for Siemens restore)
- Embedded historic project backups: **9**
- WinCC Unified generated runtime project metadata present: **Yes**

## Declared engineering versions

From `ProjectInfo.txt` contained in the uploaded Siemens archive:

```text
TiaPortal:
  MinimumRequired:
  - Version: V21.0
  - TechnicalVersion: 21.00.00.00
  LastUsed:
  - Version: V21 Update 3
  - TechnicalVersion: 21.00.03.00

UsedProducts:
- Name: STEP 7 Professional
  Version: V21
  TechnicalVersion: 21.00.00.00
- Name: Totally Integrated Automation Portal
  Version: V21
  TechnicalVersion: 21.00.00.00
- Name: WinCC Unified
  Version: V21 Update 1
  TechnicalVersion: 21.00.01.00
```

## What was **not** validated

- Actual restore/open in Siemens TIA Portal V21.
- PLC block compilation or consistency of every FB/DB/UDT in this saved archive.
- That archive bytes exactly match the PLC image exercised in the screenshots.
- Full project build from the historical plain-text SCL body snapshots.
- Safety certification or physical-machine operation (out of scope).

## Public distribution review required

The archive includes historical embedded `.zap21` backups, generated WinCC Unified runtime files and user-management/runtime configuration under `IM/HMI`. Before publishing it as a GitHub Release asset, the author should review the project in TIA Portal for user names, passwords, runtime security settings, IP addresses, hostnames, licenses, third-party assets and unnecessary backups. **Do not modify the ZIP manually** to remove Siemens project files; re-archive a cleaned project using TIA Portal.

This public-repository ZIP does not contain the binary archive, Siemens fonts or generated runtime assets.
