# PR Title

whatsapp: stop gating explicit outbound targets on allowFrom

## Concise Summary

Allow explicit outbound WhatsApp targets to bypass `allowFrom` gating while keeping implicit routing on the existing allowlist-backed path.

## Problem

Explicit outbound sends to valid E.164 targets were being rejected if the target was not also present in `allowFrom`, even though `allowFrom` is intended to control implicit routing and inbound authorization.

## Fix

- Accept valid normalized direct targets immediately when `mode === "explicit"`.
- Preserve existing gating for implicit and heartbeat-style routing.
- Add regression coverage proving explicit valid E.164 targets outside `allowFrom` succeed while implicit targets still fail.

## Tests

- `corepack pnpm exec vitest run src/whatsapp/resolve-outbound-target.test.ts`
- Result:
  - `Test Files 1 passed (1)`
  - `Tests 22 passed (22)`

## Risks / Limitations

- Low risk. This narrows allowlist enforcement to the modes that already represent implicit/allowlist-backed routing.
