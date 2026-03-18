# Changelog

All notable changes to this repository should be documented here.

The repository uses export tags instead of package versions.

## Format

- One section per published export tag
- Keep entries sanitized and upstream-safe
- Prefer semantic fix summaries over local operational detail

## [upstream-patches-20260316T175309+0100] - 2026-03-16

### Added

- Initial sanitized upstream patch export for WhatsApp explicit outbound targets
- Public issue note for the WhatsApp listener/runtime mismatch
- PR-style patch summary for the explicit target fix

### Fixed

- Explicit WhatsApp outbound targets outside `allowFrom` are accepted for explicit delivery mode

### Notes

- This repository intentionally excludes local phone numbers, machine paths, and private runbooks
- Listener/runtime mismatch is documented here as an upstream issue note, not as a local dist hotfix
