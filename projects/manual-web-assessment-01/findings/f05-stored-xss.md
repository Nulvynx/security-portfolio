# F-05 Stored Cross-Site Scripting

**Status:** Confirmed

## Summary

The assessment confirmed that user-controlled content could be stored by the application and later rendered in a browser context without sufficient output handling, resulting in stored cross-site scripting.

## Technical Details

The vulnerable flow accepted attacker-controlled input, persisted it, and subsequently rendered that content in a context where browser-executable markup or script was interpreted. The underlying issue is insufficient context-aware output encoding and/or unsafe rendering of stored untrusted data.

The public version omits the original input location, payload, affected page, identifiers, and application-specific response content.

## Validation

A controlled payload was submitted through the affected input path, stored by the application, and later rendered in the relevant browser context. Execution occurred when the stored content was viewed, confirming persistence and execution rather than reflected behavior.

## Impact

Stored XSS can allow attacker-controlled script execution in the browser context of users who view the affected content. Depending on application functionality and browser-accessible data, this can enable unauthorized actions or access to sensitive information available to the affected session.

## Remediation

Apply context-aware output encoding at every rendering sink that handles untrusted data. Avoid unsafe DOM or template rendering patterns and use framework mechanisms that escape output by default.

Input validation can reduce unwanted content but should not replace correct output encoding. Where rich content is required, use a well-maintained allowlist-based sanitizer appropriate for the rendering context.

## Retest

Submit the original test input after remediation and render the stored value in the affected view. The content should be displayed as inert data or safely sanitized, with no browser script execution.
