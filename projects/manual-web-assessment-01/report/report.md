# Penetration Test Report

## Executive Summary

A manual grey-box security assessment was performed against an explicitly authorized web application. Testing focused on authentication, session management, authorization, user-controlled input, exposed functionality, and related application security controls.

Eight security findings were confirmed. The most important recurring themes were weaknesses in server-side authorization enforcement, authentication and session lifecycle controls, untrusted input handling, and exposure of functionality that should have been more tightly restricted.

The public version of this report is intentionally sanitized and excludes information that could identify the original organization or environment.

## Assessment Overview

| Field | Value |
| --- | --- |
| Assessment Type | Web Application Penetration Test |
| Classification | Authorized Assessment |
| Approach | Grey Box |
| Testing Style | Primarily Manual |
| Status | Completed |

## Scope and Limitations

Testing was limited to the authorized web application and the functionality available through the provided assessment access.

The review covered authentication flows, session lifecycle behavior, object-level and function-level authorization, user-controlled input, diagnostic functionality, and protections against repeated authentication attempts.

Destructive testing and activity outside the explicitly authorized target were not performed.

All public material has been generalized or sanitized. Original domains, endpoint names where identifying, account data, credentials, session material, identifiers, payload values, response data, and organization-specific information are excluded.

## Methodology

The application was first mapped to identify accessible functionality, trust boundaries, authentication state, user-controlled inputs, and security-sensitive workflows.

Testing then used a baseline-and-modification approach: expected behavior was established first, followed by controlled changes to security-relevant request elements or authentication context. Potential weaknesses were treated as hypotheses until repeatable behavior demonstrated a security impact.

Confirmed findings were documented with technical explanation, validation steps, impact analysis, remediation guidance, and retest criteria.

## Risk Classification

Each public finding is classified by its confirmed technical behavior together with the applicable CWE and OWASP Top 10 category.

Numeric severity and CVSS scores are not inferred from vulnerability class alone. Where accurate scoring depends on environment-specific assumptions that are intentionally excluded from the public record, the sanitized portfolio version omits the numeric score rather than presenting unsupported precision.

## Findings Summary

| ID | Finding |
| --- | --- |
| F-01 | [Boolean-Based SQL Injection](../findings/f01-sql-injection.md) |
| F-02 | [Session Revocation Failure](../findings/f02-session-revocation.md) |
| F-03 | [Broken Object-Level Authorization](../findings/f03-object-level-authorization.md) |
| F-04 | [Exposed Diagnostic Endpoint](../findings/f04-diagnostic-endpoint.md) |
| F-05 | [Stored Cross-Site Scripting](../findings/f05-stored-xss.md) |
| F-06 | [Missing Function-Level Authorization](../findings/f06-function-level-authorization.md) |
| F-07 | [Authentication Replay](../findings/f07-authentication-replay.md) |
| F-08 | [Insufficient Protection Against Repeated Authentication Attempts](../findings/f08-authentication-rate-limiting.md) |

See the [finding classification mapping](../findings/classification.md) for CWE and OWASP Top 10:2025 mappings.

## Detailed Findings

Detailed technical descriptions are maintained as individual finding documents so that each issue can be reviewed, updated, and retested independently.

- [F-01 Boolean-Based SQL Injection](../findings/f01-sql-injection.md)
- [F-02 Session Revocation Failure](../findings/f02-session-revocation.md)
- [F-03 Broken Object-Level Authorization](../findings/f03-object-level-authorization.md)
- [F-04 Exposed Diagnostic Endpoint](../findings/f04-diagnostic-endpoint.md)
- [F-05 Stored Cross-Site Scripting](../findings/f05-stored-xss.md)
- [F-06 Missing Function-Level Authorization](../findings/f06-function-level-authorization.md)
- [F-07 Authentication Replay](../findings/f07-authentication-replay.md)
- [F-08 Insufficient Protection Against Repeated Authentication Attempts](../findings/f08-authentication-rate-limiting.md)

## Technical Evidence

Sanitized HTTP-level reconstructions are maintained separately from the finding narratives so that the report stays readable while technical reviewers can inspect the validation logic.

[Review the technical evidence index](../evidence/README.md).

## Remediation Priorities

### 1. Authorization Enforcement

Review authorization controls at both object and function level. Security decisions should be enforced server-side for every protected operation and should be based on explicit ownership, role, permission, or policy relationships.

Relevant findings: F-03, F-06.

### 2. Authentication and Session Lifecycle

Strengthen the lifecycle of authentication and session material, including logout revocation, replay resistance, and protection against sustained authentication attempts.

Relevant findings: F-02, F-07, F-08.

### 3. Untrusted Input Handling

Ensure untrusted input cannot alter backend query structure and cannot be rendered in executable browser contexts. Use parameterized database access and context-aware output encoding at the appropriate trust boundaries.

Relevant findings: F-01, F-05.

### 4. Production Exposure

Remove or appropriately restrict diagnostic functionality that is not intended for ordinary application users.

Relevant finding: F-04.

## Conclusion

The assessment identified multiple confirmed weaknesses across independent application security controls. Remediation should address not only individual vulnerable requests but also the broader control patterns behind them, particularly authorization enforcement, authentication state management, and safe handling of untrusted input.

A retest should verify both the originally affected functionality and comparable application paths that rely on the same security controls.
