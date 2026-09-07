# F-06 Technical Validation

> Sanitized reconstruction. The original privileged function, role names, identifiers, and response content are replaced with neutral examples.

## Expected privilege boundary

The application workflow indicated that the tested action was intended for a more privileged authorization context.

## Direct invocation from a lower-privileged session

```http
POST /admin/action HTTP/1.1
Host: app.example.test
Cookie: session=[lower-privileged-session]
Content-Type: application/json

{"resource_id":1001,"action":"update"}
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

{"status":"completed"}
```

## Security conclusion

The backend processed a restricted function while the caller remained authenticated in a lower-privileged context. The weakness resulted from missing server-side function-level authorization.
