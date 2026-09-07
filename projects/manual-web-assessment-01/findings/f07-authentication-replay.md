# F-07 Authentication Replay

**Status:** Confirmed

## Summary

The assessment confirmed that a previously captured authentication artifact could be reused to reproduce an authenticated outcome without completing a fresh authentication exchange.

## Technical Details

The affected authentication flow accepted a reusable credential-equivalent artifact without sufficient freshness or one-time-use guarantees. This weakens the intended boundary between possession of a captured authentication value and successful authentication.

The public version intentionally omits the original artifact format, request structure, endpoint details, account data, and environment-specific values.

## Validation

A valid authentication exchange was first completed and the relevant client-supplied authentication material was captured. The same material was then replayed in a subsequent request without performing a new authentication step. The application accepted the replayed value and reproduced the authenticated behavior.

## Impact

If an attacker obtains the reusable authentication artifact, they may be able to authenticate by replaying it rather than supplying the user's original secret or completing the expected authentication flow. The practical risk depends on the artifact lifetime, transport protections, and conditions under which it can be obtained.

## Remediation

Avoid treating replayable client-supplied values as sufficient proof of a fresh authentication event. Use short-lived, server-validated authentication state and introduce freshness guarantees where the protocol requires them, such as nonces, one-time challenges, or single-use transaction state.

Ensure captured authentication material cannot be reused beyond its intended context or lifetime.

## Retest

Repeat a valid authentication exchange, capture the relevant authentication material, and attempt to reuse it in a new authentication attempt. Previously used or stale material should be rejected and a fresh authentication exchange should be required.
