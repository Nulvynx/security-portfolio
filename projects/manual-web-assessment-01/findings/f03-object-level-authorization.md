# F-03 Broken Object-Level Authorization

| Field | Value |
| --- | --- |
| Status | Confirmed |
| CWE | CWE-639: Authorization Bypass Through User-Controlled Key |
| OWASP Top 10 | A01:2025 Broken Access Control |

## Summary

The assessment confirmed that an authenticated user could access an object outside the expected ownership boundary by modifying a client-controlled object reference.

## Technical Details

Authentication was enforced, but object-level authorization was not consistently applied before returning the requested resource. The application trusted a user-supplied identifier without sufficiently verifying that the authenticated principal was authorized to access the referenced object.

The public version uses neutral terminology and omits original identifiers, account data, endpoint details, and response content.

## Validation

A legitimate request was first established for an object available to the authenticated test account. The object reference was then changed while preserving the same authenticated session. The application returned an object outside the expected authorization boundary, confirming the access-control failure.

## Evidence

[Review the sanitized HTTP validation](../evidence/f03-validation.md).

## Impact

Successful exploitation allows an authenticated user to access resources that should be restricted to another authorization context. The resulting impact depends on the sensitivity and operations exposed by the affected object.

## Remediation

Enforce object-level authorization on the server for every request that references a protected resource. Authorization decisions should be based on the authenticated principal and explicit ownership or access relationships, not on knowledge or unpredictability of an object identifier.

Using non-sequential identifiers can reduce enumeration but must not replace authorization controls.

## Retest

Repeat the test using separate accounts or authorization contexts with distinct object ownership. A request for an object outside the caller's authorization boundary should be rejected without exposing the protected resource.
