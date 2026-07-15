# DJConnect Firmware Distribution Bootstrap

This repository distributes public ESP32 artifacts only. It adopts AI-Native
Engineering Operating System 2.2 from
`pcvantol/djconnect/docs/governance/PLATFORM_ARCHITECT_SYSTEM_INSTRUCTIONS.md`
by reference and never copies central governance.

Start with `git switch main`, `git pull --ff-only`, current-main/clean-tree and
predecessor verification. Read local status, roadmap and prompt index;
reconcile `MERGED_UNRECONCILED` before work and perform an implementation-
reality check. Lifecycle is `LOCAL_IN_PROGRESS`, `REVIEWABLE_FROZEN`,
`MERGED_UNRECONCILED`, `MERGED_RECONCILED`; cleanup is fail-closed.
