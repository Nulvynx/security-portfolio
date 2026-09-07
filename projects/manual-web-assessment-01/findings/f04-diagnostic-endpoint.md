# F-04 Exposed Diagnostic Endpoint

| Field | Value |
| --- | --- |
| Status | Confirmed |
| CWE | CWE-489: Active Debug Code |
| OWASP Top 10 | A02:2025 Security Misconfiguration |

## Summary

The assessment confirmed that diagnostic functionality was exposed through an application endpoint that was reachable in the assessed environment.

## Technical Details

Diagnostic endpoints can disclose implementation details, operational state, configuration data, or internal behavior that is not intended for normal users. Even where the exposed information is not directly exploitable on its own, unnecessary diagnostic exposure can reduce uncertainty for an attacker and increase the usefulness of other weaknesses.

The public version does not reproduce the original endpoint, response body, product identifiers, or environment-specific data.

## Validation

The endpoint was requested directly and returned diagnostic content without the level of restriction expected for non-user-facing functionality.

## Impact

The primary risk is information exposure and unnecessary expansion of the application's observable attack surface. The practical impact depends on the sensitivity of the diagnostic data returned by the endpoint.

## Remediation

Remove diagnostic functionality from production-facing deployments where it is not required. If operational access is necessary, restrict it through appropriate authentication and authorization controls and minimize the information returned.

Review deployment configuration to ensure debug and diagnostic features are disabled by default outside intended administrative environments.

## Retest

Attempt to access the previously exposed diagnostic functionality from an ordinary application context. The endpoint should either be unavailable or enforce the intended administrative access controls without disclosing sensitive diagnostic data.
