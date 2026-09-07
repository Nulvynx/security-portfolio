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

Security testing included authentication flows, session lifecycle controls, object-level and function-level authorization, user-controlled input handling, exposed application functionality, repeated authentication attempts, and security configuration relevant to the accessible attack surface.

Destructive testing and activities outside the authorized target were not performed.

## Methodology

The application was first mapped to establish accessible functionality, trust boundaries, authentication state, user-controlled inputs, and security-relevant workflows.

Testing then focused on establishing expected application behavior and deliberately modifying security-relevant inputs or request context to validate whether controls were enforced server-side. Potential issues were treated as hypotheses until reproducible behavior confirmed a security impact.

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

Numeric severity and CVSS scores are not inferred from vulnerability names. They are included in public material only when the scoring rationale can be reproduced without relying on confidential environment-specific assumptions.

## Technical Evidence

Each finding is supported by a sanitized HTTP-level reconstruction showing the relevant baseline, controlled change, and observed security result. The reconstructions preserve the request method, security boundary, and validation sequence where those details matter, while replacing identifying paths, parameter names, credentials, session values, and response data.

[Review technical evidence](evidence/README.md).

## Security Themes

The confirmed findings affected several distinct control areas, with recurring themes around server-side authorization enforcement, authentication and session lifecycle controls, safe handling of untrusted input, exposure of diagnostic functionality, and protection against repeated authentication attempts.

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

A sanitized penetration test report accompanies this project and excludes information that could identify the original environment.

[Read the sample penetration test report](report/report.md).

## Tooling

**Burp Suite Community Edition** was used for manual HTTP interception, request history analysis, replay, and controlled request modification through Proxy and Repeater. A standard web browser was used to exercise application workflows and confirm browser-side behavior where relevant.
