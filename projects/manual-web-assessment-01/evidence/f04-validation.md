# F-04 Technical Validation

> Sanitized reconstruction. The original diagnostic path, product identifiers, and response content are intentionally not reproduced.

## Direct request

```http
GET /diagnostics HTTP/1.1
Host: app.example.test
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "status": "ok",
  "runtime": "[redacted]",
  "environment": "[redacted]"
}
```

## Security conclusion

Diagnostic functionality was directly reachable from the assessed application context and returned operational information not required for normal user functionality.
