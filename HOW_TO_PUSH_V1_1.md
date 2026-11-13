# Push this v1.1 package using GitHub Desktop

**Important: This is a documentation/evidence and reference-source update package. Final v1.1 authoritative SCL export is not included yet.**

1. Download/extract this ZIP to a temporary folder.
2. In **GitHub Desktop**, select the existing repository `siemens-s7-1500-robotic-cnc-cell` and checkout **`v1.1-development`**. Do **not** create another repo.
3. Choose **Repository → Show in Explorer**. Open the extracted package folder in another Explorer window.
4. Copy all *contents* of the extracted folder into the existing repo root, accepting merges/overwrites. Do NOT replace or delete the hidden `.git` folder in your repo.
5. The original v1.0 source has moved to `plc/baseline_v1.0`. Remove the old `plc/exported/PLC_CNC_Cell_Full_Source_Export.scl` from the working repo if Windows copying left it behind; otherwise reviewers may mistake it for the new v1.1 source.
6. When you export final v1.1 code from TIA Cloud, add it to `plc/exported/PLC_CNC_Cell_v1.1_Final_Source_Export.scl`. Keep the old baseline under `plc/baseline_v1.0`.
7. In GitHub Desktop's **Changes** tab, inspect the added evidence and updated files, and ensure no private `.zap21`/credentials are staged. Commit as `Document v1.1 automatic production and fault recovery` and click **Push origin**.
8. After final source and remaining tests are verified, create PR `v1.1-development → main`, merge, and publish a **v1.1.0** release using `RELEASE_NOTES_v1.1_DRAFT.md` as a starting point.

If your repository already has v1.1 code edits, do not overwrite them with the reference files in this package; keep the authoritative current export.
