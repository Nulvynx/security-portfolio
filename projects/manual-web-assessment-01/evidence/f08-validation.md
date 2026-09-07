# F-08 Technical Validation

> Sanitized reconstruction. The original authentication route, parameter names, tested account, attempt count, timing, and environment-specific thresholds are intentionally not reproduced.

## Repeated authentication sequence

Representative authentication requests were submitted in sequence using invalid credentials:

```http
POST / HTTP/1.1
Host: app.example.test
Content-Type: application/x-www-form-urlencoded

action=login&username=[test-user]&credential=[invalid-value]&state=[redacted]
```

The application returned its normal authentication-failure behavior and continued to process subsequent attempts.

Across the controlled sequence, no effective server-side response materially interrupted sustained guessing activity through throttling, progressive delay, temporary blocking, or an equivalent control.

## Security conclusion

The finding is based on the absence of an effective control during repeated authentication attempts, not merely on the absence of a visible CAPTCHA or a particular user-interface mechanism.
