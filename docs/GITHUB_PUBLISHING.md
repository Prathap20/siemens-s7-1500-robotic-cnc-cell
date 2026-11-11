# Publish first release using GitHub

## Before going public

- The source export is already under `plc/exported/PLC_CNC_Cell_Full_Source_Export.scl`. Keep it as the only combined SCL source; do not upload the overlapping root-level `PLC_CNC_Cell.scl`.
- Keep the unreviewed TIA archive private; if you later re-archive a cleaned project, attach it as a Release asset, not as a normal Git commit.
- Check no passwords, organization secrets, private contact details or license-restricted assets are included.
- Keep `plc/reference_snapshots/` as clearly labelled earlier code fragments, not the importable software source.

## Browser route

1. On GitHub, create a public repository named `siemens-s7-1500-robotic-cnc-cell` (do not initialize README or license if uploading the current complete folder).
2. Use **Add file → Upload files** to upload the unzipped folder CONTENTS to repository root (GitHub does not automatically unpack a ZIP).
3. Commit with message `Release v1.0: verified robotic CNC simulation and WinCC HMI`.
4. After checking README images and archive paths, use **Releases → Draft a new release → New tag `v1.0.0`**; describe known limitations and attach archive as release asset if the archive is too large for browser file upload.
5. Copy repository URL into LinkedIn Featured and CV after verifying it is publicly accessible.

## Git command line alternative

```powershell
git init
git add .
git commit -m "Release v1.0: robotic CNC cell and WinCC Unified HMI"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/siemens-s7-1500-robotic-cnc-cell.git
git push -u origin main
```

If an existing repository already contains a commit, clone it first rather than force-pushing over its history.

GitHub browser upload file limit is 25 MiB per file; files beyond this require command line, a Release asset or Git LFS depending on size. See https://docs.github.com/en/repositories/working-with-files/managing-files/adding-a-file-to-a-repository

## Next release

After tagging `v1.0.0`, create a separate `feature/auto-fault-scenarios` branch; preserve the baseline commit so the tested release is reproducible. Do not present v1.1 plans as shipped functionality.
