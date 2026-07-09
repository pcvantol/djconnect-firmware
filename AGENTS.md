# DJConnect Firmware Release Agent Instructions

## DJConnect Platform Bootstrap

For a clean Codex/AI-agent session, first follow the canonical platform bootstrap:

`pcvantol/djconnect/BOOTSTRAP_CODEX_SESSION.md`

Then continue with the repository-specific instructions in this file.

This repository extends the DJConnect Platform Foundation. It does not redefine it.

This must be additive only. Existing repo-specific AGENTS guidance remains authoritative for implementation details.


This repository follows the canonical DJConnect design foundation in `pcvantol/djconnect`.

Read first:

- `pcvantol/djconnect/DJCONNECT_CONSTITUTION.md`
- `pcvantol/djconnect/ARCHITECTURE_PRINCIPLES.md`
- `pcvantol/djconnect/PLATFORM_GOVERNANCE.md`
- `pcvantol/djconnect/PLATFORM_QUALITY_STANDARD.md`
- `pcvantol/djconnect/SYNC_PROMPTS.md`
- `pcvantol/djconnect/PRODUCT_ROADMAP.md`

## Role

This repo is a distribution surface for public DJConnect ESP32 firmware releases.

It publishes artifacts, manifests and release notes. It does not own product logic, firmware source, platform contracts or roadmap decisions.

## Rules

- Do not add firmware source logic here.
- Do not fork roadmap, sync prompts or product contracts locally.
- Release artifacts should be traceable to source commits in `pcvantol/djconnect-esp32`.
- Release notes should describe user-visible behavior and compatibility.
- Do not publish secrets, signing keys, tokens, WiFi credentials, Home Assistant tokens or provider credentials.
- Artifact integrity should be preserved with hashes/checksums where supported.
- Keep release behavior aligned with `PLATFORM_QUALITY_STANDARD.md`.
