# F-02 Technical Validation

> Sanitized reconstruction. Session values, paths, and response data are neutralized and do not reproduce the original target environment.

## Authenticated baseline

```http
GET /account HTTP/1.1
Host: app.example.test
Cookie: session=[captured-session]
```

```http
HTTP/1.1 200 OK

[authenticated account content]
```

## Logout

```http
POST /logout HTTP/1.1
Host: app.example.test
Cookie: session=[captured-session]
```

The normal logout flow completed successfully.

## Reuse of the pre-logout session

```http
GET /account HTTP/1.1
Host: app.example.test
Cookie: session=[captured-session]
```

```http
HTTP/1.1 200 OK

[authenticated account content]
```

## Security conclusion

The same session credential remained accepted after logout, demonstrating ineffective server-side revocation.
