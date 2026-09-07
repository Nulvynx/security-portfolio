# F-02 Session Revocation Failure

**Status:** Confirmed

## Summary

The assessment confirmed that a previously authenticated session remained usable after the user completed the logout flow. This indicates that logout did not reliably revoke the server-side session state associated with the session credential.

## Technical Details

A secure logout process should invalidate the active session so that possession of an old session identifier is no longer sufficient to access authenticated functionality. In the observed case, the session credential could still be used after logout, showing that client-side logout behavior was not matched by effective server-side revocation.

The public version omits original session values, endpoint details, cookies, and environment-specific responses.

## Validation

The session was established through normal authentication, the logout flow was completed, and the previously issued session credential was then reused against authenticated functionality. Access remained possible, confirming ineffective session revocation.

## Impact

If a valid session credential is copied or otherwise obtained, logout may not terminate the attacker's ability to use that credential. This weakens user expectations around session termination and can extend the useful lifetime of a compromised session.

## Remediation

Invalidate the corresponding server-side session as part of logout. Do not rely only on deleting or expiring the browser cookie. Where session stores are used, remove or revoke the active session record and ensure subsequent requests using the old credential are rejected.

## Retest

Authenticate, capture the issued session credential, log out, and repeat an authenticated request using the pre-logout credential. The application should reject the request and require a new authenticated session.
