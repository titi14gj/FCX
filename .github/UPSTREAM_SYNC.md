# Upstream sync automation

This fork keeps the original project at `z3183644/FCX` as its upstream source and
maintains the macOS work on `agent/add-macos-liquid-glass-client`.

The `Sync upstream FCX` workflow runs every Monday at 11:20 China Standard Time
and can also be started manually from the Actions page. When upstream has new
commits, it:

1. merges upstream `main` into a temporary `automation/upstream-*` branch;
2. runs the complete userscript checks and backend tests on Windows and macOS;
3. builds the macOS application package;
4. opens a draft pull request into the macOS maintenance branch only after all
   checks pass.

If the merge conflicts, the workflow opens an issue listing the conflicting
files. If validation fails, it opens an issue linking to the failed workflow run.
It never merges a pull request automatically.

To use a different maintenance branch, run the workflow manually and enter that
branch in the `target_branch` input.
