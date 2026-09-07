# F-06 Missing Function-Level Authorization

| Field | Value |
| --- | --- |
| Status | Confirmed |
| CWE | CWE-862: Missing Authorization |
| OWASP Top 10 | A01:2025 Broken Access Control |

## Summary

The assessment confirmed that restricted application functionality could be invoked from an authorization context that should not have been permitted to perform the action.

## Technical Details

The affected function relied on access assumptions that were not consistently enforced server-side. Although the functionality was intended for a more privileged context, the backend accepted a direct request from a lower-privileged authenticated context.

The public version omits the original function name, endpoint, account roles, identifiers, and response content.

## Validation

The expected authorization boundary was first established using the application workflow. The restricted function was then requested directly while preserving a lower-privileged authenticated session. The application processed the request instead of enforcing the intended function-level restriction.

## Evidence

[Review the sanitized HTTP validation](../evidence/f06-validation.md).

## Impact

Successful exploitation can allow a user to perform actions outside the privileges assigned to their account. The resulting impact depends on the capability exposed by the affected function and the data or state it can modify.

## Remediation

Enforce function-level authorization on the server for every privileged action. Authorization checks should be based on the authenticated principal and the application's explicit role, permission, or policy model rather than on whether a function is hidden from the user interface.

Centralize authorization logic where practical and apply deny-by-default behavior to privileged operations.

## Retest

Repeat the restricted request using an account that does not possess the required permission. The application should reject the operation and should not perform any associated state change.
