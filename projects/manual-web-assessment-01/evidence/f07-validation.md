# F-07 Technical Validation

> Sanitized reconstruction. The original authentication artifact, request structure, endpoint, and account data are not reproduced.

## Initial authentication exchange

```http
POST /auth/verify HTTP/1.1
Host: app.example.test
Content-Type: application/x-www-form-urlencoded

auth_value=[fresh-artifact]
```

The application accepted the value and established the expected authenticated outcome.

## Replay

The same client-supplied authentication value was then reused without completing a new authentication exchange:

```http
POST /auth/verify HTTP/1.1
Host: app.example.test
Content-Type: application/x-www-form-urlencoded

auth_value=[same-captured-artifact]
```

The application accepted the replayed value again.

## Security conclusion

The tested artifact behaved as a reusable password-equivalent rather than as proof of a fresh authentication event. The finding therefore concerns replay resistance and freshness of authentication material.
