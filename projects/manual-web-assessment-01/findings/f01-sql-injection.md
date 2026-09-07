# F-01 Boolean-Based SQL Injection

| Field | Value |
| --- | --- |
| Status | Confirmed |
| CWE | CWE-89: Improper Neutralization of Special Elements used in an SQL Command |
| OWASP Top 10 | A05:2025 Injection |

## Summary

The assessment confirmed that user-controlled input could influence a backend SQL query in a way that allowed boolean-based SQL injection. Controlled true/false conditions produced distinguishable application behavior, demonstrating that the input was not safely isolated from the query structure.

## Technical Details

The vulnerable behavior indicates that untrusted input reached a database query without adequate parameterization or equivalent query-safety controls. This creates a condition in which an attacker can alter query logic rather than supplying data only.

The public version intentionally omits the original parameter names, endpoint details, payload values, and environment-specific responses.

## Validation

The issue was validated by establishing normal application behavior and comparing it with responses produced by controlled boolean conditions. The result was treated as confirmed only after the behavior was repeatable.

## Impact

Successful exploitation can allow an attacker to manipulate database query logic. The exact impact depends on the affected query, database permissions, and reachable data paths.

## Remediation

Use parameterized queries or prepared statements for all database operations involving untrusted input. Do not construct SQL statements through string concatenation. Apply server-side input validation as defense in depth, but do not treat validation as a replacement for parameterization.

Database accounts should also operate with the minimum privileges required by the application.

## Retest

Repeat the original true/false test cases after remediation. User input should be handled strictly as data and should no longer influence SQL query structure or produce query-dependent behavioral differences.
