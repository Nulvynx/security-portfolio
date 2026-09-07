# Security Assessment Portfolio

Practical portfolio focused on penetration testing, application security, security assessment methodology, and technical reporting.

The work published here demonstrates the assessment process from application mapping and security hypotheses through manual validation, evidence collection, risk analysis, remediation, and reporting.

## Selected Work

### Manual Web Application Penetration Test

**Authorized Assessment · Web Application · Grey Box**

Manual security assessment of a controlled web application covering authentication, session management, authorization, input handling, exposed functionality, and security controls.

The assessment resulted in eight confirmed security findings, including:

- Boolean-based SQL injection
- Session revocation failure
- Broken object-level authorization
- Exposed diagnostic functionality
- Stored cross-site scripting
- Missing function-level authorization
- Authentication replay
- Insufficient protection against repeated authentication attempts

The project includes a concise assessment case study, individual technical findings with CWE and OWASP classification, and a sanitized sample penetration test report.

[View assessment](projects/manual-web-assessment-01/README.md) · [Technical findings](projects/manual-web-assessment-01/findings/) · [Sample report](projects/manual-web-assessment-01/report/report.md)

## What This Portfolio Demonstrates

Projects focus on the parts of security assessments that matter in real engagements:

- application and attack-surface mapping
- authentication and session analysis
- authorization modelling and access-control testing
- manual HTTP request analysis and manipulation
- vulnerability validation
- exploitation reasoning
- evidence collection
- root cause analysis
- CWE and OWASP classification
- risk assessment
- remediation design
- retest planning
- technical and executive reporting

Confirmed findings, observations, negative results, hypotheses, and testing limitations are treated separately where relevant.

## Areas of Focus

Current work is primarily focused on:

- Web Application Security
- API Security
- Authentication and Authorization
- Application Security
- Secure Code Review
- Vulnerability Assessment
- Penetration Testing Methodology
- Security Reporting

Additional areas are added only when supported by completed technical work.

## Reporting Approach

A useful security finding should allow another tester to understand and reproduce the issue, a developer to understand the root cause and remediation, and a decision-maker to understand the security impact.

Projects therefore prioritize:

**scope → methodology → validation → evidence → impact → remediation → retest**

## Publication Standard

This repository contains only material suitable for public disclosure. Published assessment material is sanitized and does not include client names, real domains, credentials, authentication tokens, session data, internal identifiers, proprietary source code, or other information that could identify or expose an original environment.

Projects are described according to their actual context. Labs, research, bug bounty work, controlled assessments, and other project types are not presented as commercial engagements unless that accurately reflects the work performed.
