# Firmware distribution governance reconciliation

Finalization of [PR #8](https://github.com/pcvantol/djconnect-firmware/pull/8), merged as `c525d6a3c69f8cf45bd5cbd06f2cbac2cac9082e`.
Admission main `2b6a6936decff63d94c1ed3af53c46ba7888dfd6` contains that predecessor and later maintenance. Four stale rolling records are reconciled as one body; existing immutable history remains unchanged.

Scope is exactly four rolling records and this new immutable history entry. No README branding, firmware binaries, manifest, release workflow, source, credentials, contracts or hardware is changed. No historical CI or installed qualification is fabricated. Brand V2 README adoption remains a separately reviewed source increment after reconciliation/readiness.

Validation before push: canonical Core lifecycle regression seven tests PASS (run read-only in its owning repo); four-record equality and diff hygiene PASS. Independent review, exact-SHA CI and applicable authorization are separate protected-merge gates. Cleanup and actual main equality are verified after merge.
