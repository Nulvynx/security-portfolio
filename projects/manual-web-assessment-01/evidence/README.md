# Technical Evidence

This directory contains sanitized technical reconstructions of the validation logic used for each confirmed finding.

The examples preserve the relevant request method, transport shape, security boundary, controlled modification, and observed result where those details are important to understanding the finding. Original paths, parameter names, account data, credentials, session material, payload values, response content, and other environment-specific details are replaced or generalized.

They are intended to show how each finding was technically confirmed without exposing the original assessment environment.

| Finding | Technical validation |
| --- | --- |
| F-01 | [Boolean-Based SQL Injection](f01-validation.md) |
| F-02 | [Session Revocation Failure](f02-validation.md) |
| F-03 | [Broken Object-Level Authorization](f03-validation.md) |
| F-04 | [Exposed Diagnostic Endpoint](f04-validation.md) |
| F-05 | [Stored Cross-Site Scripting](f05-validation.md) |
| F-06 | [Missing Function-Level Authorization](f06-validation.md) |
| F-07 | [Authentication Replay](f07-validation.md) |
| F-08 | [Repeated Authentication Attempts](f08-validation.md) |
