# Manual Web Application Penetration Test

**Authorized Assessment · Web Application · Grey Box**

## Overview

This project documents a manual security assessment of a controlled web application performed within an explicitly authorized scope.

The assessment focused on identifying and validating security weaknesses in authentication, session management, authorization, input handling, exposed functionality, and related application controls. Testing emphasized manual verification and reproducible evidence rather than automated finding counts.

Eight security findings were confirmed during the assessment.

## Assessment Context

| Field | Value |
| --- | --- |
| Classification | Authorized Assessment |
| Target Type | Web Application |
| Approach | Grey Box |
| Testing Style | Primarily Manual |
| Status | Completed |

All public material in this project is sanitized. Original organization names, domains, account data, identifiers, credentials, session material, and environment-specific information are intentionally excluded.

## Scope

The assessment covered the authorized web application and the functionality available through the provided test access.

Security testing included:

- authentication flows
- session lifecycle controls
- object-level authorization
- function-level authorization
- user-controlled input handling
- exposed application functionality
- repeated authentication attempts
- application security configuration relevant to the accessible attack surface

Destructive testing and activities outside the authorized target were not performed.

## Methodology

The application was first mapped to establish the accessible functionality, trust boundaries, authentication state, user-controlled inputs, and security-relevant workflows.

Testing then focused on establishing expected application behavior and deliberately modifying security-relevant inputs or request context to validate whether controls were enforced server-side. Potential issues were treated as hypotheses until reproducible behavior confirmed a security impact.

Confirmed findings were documented with impact analysis, remediation guidance, and retest considerations. Environment-specific proof material is published only where it can be sanitized without weakening confidentiality.

## Key Findings

| ID | Finding |
| --- | --- |
| F-01 | [Boolean-Based SQL Injection](findings/f01-sql-injection.md) |
| F-02 | [Session Revocation Failure](findings/f02-session-revocation.md) |
| F-03 | [Broken Object-Level Authorization](findings/f03-object-level-authorization.md) |
| F-04 | [Exposed Diagnostic Endpoint](findings/f04-diagnostic-endpoint.md) |
| F-05 | [Stored Cross-Site Scripting](findings/f05-stored-xss.md) |
| F-06 | [Missing Function-Level Authorization](findings/f06-function-level-authorization.md) |
| F-07 | [Authentication Replay](findings/f07-authentication-replay.md) |
| F-08 | [Insufficient Protection Against Repeated Authentication Attempts](findings/f08-authentication-rate-limiting.md) |

CWE and OWASP Top 10 mappings are documented in each finding and summarized in the [classification mapping](findings/classification.md).

Numeric severity and CVSS scores are not inferred from vulnerability names. They are included in public material only when the underlying scoring rationale can be reproduced without relying on confidential environment-specific assumptions.

## Security Themes

The confirmed findings affected several distinct control areas, with recurring themes around:

- server-side authorization enforcement
- authentication and session lifecycle controls
- safe handling of untrusted input
- exposure of diagnostic functionality
- protection against repeated authentication attempts

The assessment therefore demonstrated the importance of addressing both individual vulnerabilities and the underlying security controls that allow related weaknesses to occur.

## Skills Demonstrated

- web application mapping
- authentication and session testing
- authorization modelling
- manual HTTP request analysis
- input validation testing
- vulnerability confirmation
- evidence collection
- root cause analysis
- risk assessment
- remediation planning
- technical reporting

## Report

A sanitized penetration test report accompanies this project. The public report is derived from the assessment material and excludes information that could identify the original environment.

[Read the sample penetration test report](report/report.md).
