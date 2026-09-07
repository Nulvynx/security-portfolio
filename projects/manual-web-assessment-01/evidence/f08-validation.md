# F-08 Technical Validation

> Sanitized reconstruction. The original authentication endpoint, tested account, timing, attempt count, and environment-specific thresholds are intentionally not reproduced.

## Repeated authentication sequence

Representative requests were submitted in sequence using invalid credentials:

```http
POST /login HTTP/1.1
Host: app.example.test
Content-Type: application/x-www-form-urlencoded

username=test-user&password=[invalid-value]
```

Representative response:

```http
HTTP/1.1 401 Unauthorized
Content-Type: application/json

{"error":"invalid credentials"}
```

Across the tested sequence, the application continued to accept authentication attempts without an effective server-side response such as material throttling, progressive delay, temporary blocking, or an equivalent control.

## Security conclusion

The finding is based on the absence of an effective control during a controlled repeated-attempt test, not merely on the absence of a visible CAPTCHA.
