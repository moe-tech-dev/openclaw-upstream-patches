# OpenClaw Upstream Patches

![Repo Type](https://img.shields.io/badge/repo-public%20upstream-238636)
![Patch Class](https://img.shields.io/badge/patches-sanitized%20source%20fixes-8250df)

Sanitized OpenClaw bugfix artifacts that are safe to share publicly.

## Included

- `patches/20260316T175309+0100-01-whatsapp-explicit-target.patch`
- `docs/20260316T175309+0100-11-pr-whatsapp-explicit-target.md`
- `docs/whatsapp-listener-runtime-mismatch.md`

## Purpose

- Keep shareable upstream-oriented fixes separate from private machine-specific hotfixes.
- Preserve a clean public history for fixes that should eventually live in OpenClaw core.

## Excluded

- No phone numbers
- No local cron job IDs
- No machine-specific reapply commands
- No absolute `/home/...` paths

## Notes

- The explicit outbound target patch is source-level and suitable for upstream review.
- The listener/runtime mismatch document is currently an issue note and semantic fix description, not a source patch.

## Changelog

- `CHANGELOG.md`

## Tag Scheme

- Format: `upstream-patches-YYYYMMDDTHHMMSS+TZ`
- First tag: `upstream-patches-20260316T175309+0100`
- Meaning: one sanitized export set intended for sharing, review, or upstream submission
