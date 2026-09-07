# F-07 Technical Validation

> Sanitized reconstruction. The original credential-derived value, account names, route, parameter names, and session material are not reproduced. The form-based login flow and replay of the same password-equivalent reflect the confirmed test.

## Initial authentication exchange

```http
POST / HTTP/1.1
Host: app.example.test
Content-Type: application/x-www-form-urlencoded

action=login&username=[privileged-user]&credential=[captured-password-equivalent]&state=[redacted]
```

The application accepted the client-supplied credential-equivalent value and returned the authenticated application context.

## Replay

The same captured value was then submitted again without knowledge of the original plaintext secret and without generating a fresh authentication proof:

```http
POST / HTTP/1.1
Host: app.example.test
Content-Type: application/x-www-form-urlencoded

action=login&username=[privileged-user]&credential=[same-captured-password-equivalent]&state=[redacted]
```

The application accepted the replayed value again.

## Security conclusion

The client-supplied credential representation functioned as a reusable password-equivalent. Capturing that value was therefore sufficient to reproduce the authentication result without obtaining the underlying plaintext password.
