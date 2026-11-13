# Push v1.1 to GitHub Desktop

This project was already published as v1.0.0. **Do not create a new repository.** Use the existing repository and `v1.1-development` branch.

1. In GitHub Desktop, select `v1.1-development` and **Repository → Show in Explorer**.
2. Extract the new v1.1 ZIP and copy its *contents* into the Git repository root; retain `.git`.
3. Keep original v1.0 SCL export under `plc/baseline_v1.0`; do not treat it as final v1.1 source.
4. Export final v1.1 combined source from TIA Portal into `plc/exported/PLC_CNC_Cell_v1.1_Final_Source_Export.scl` before official v1.1 release.
5. In GitHub Desktop inspect Changes, commit, then **Push origin**. Review the changes online on the development branch.
6. After source export and remaining tests, open pull request v1.1-development → main and publish release v1.1.0.

Detailed steps: [v1.1 source and release](V1_1_SOURCE_AND_RELEASE.md).  [v1.1 validation](V1_1_VALIDATION.md).
