# WhatsApp status/send-path mismatch

## Summary

WhatsApp channel status can report `connected: true` while the real send path still fails because no active web listener is available for the account.

## Expected behavior

- If status reports the WhatsApp account as connected, the gateway send path should be able to send.
- The status view and the send path should derive readiness from the same effective listener state.

## Actual behavior

- Status can be healthy while `requireActiveWebListener(accountId)` still fails.
- In practice this appears during startup or recovery windows and causes false-positive health reporting.

## Root cause

Two distinct issues can combine:

1. Listener lifecycle ordering is non-atomic.
   - `connected: true` can be published before the active listener is registered.
   - the listener can be removed before `connected: false` is published
2. In the affected bundled build, active-listener state was duplicated across multiple compiled chunks instead of being truly shared.

## Minimal semantic fix

- Register the active listener before publishing `connected: true`.
- Clear or downgrade connected status before removing the listener.
- Ensure all runtime chunks resolve active-listener state from one shared registry.

## Why this matters

- Health reporting otherwise overstates readiness.
- Restart recovery and stale-socket recovery can look healthy while delivery still fails.
