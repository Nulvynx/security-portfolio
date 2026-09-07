# F-06 Technical Validation

> Sanitized reconstruction. The original privileged route, action names, role labels, session material, and response content are replaced. The direct form-based invocation from a lower-privileged context reflects the confirmed test.

## Expected privilege boundary

The application workflow indicated that the tested function was intended for a privileged authorization context.

## Direct invocation from a lower-privileged state

```http
POST /?[privileged-function] HTTP/1.1
Host: app.example.test
Content-Type: application/x-www-form-urlencoded

action=privileged&state=[lower-privileged-state]
```

The backend returned the restricted administrative functionality instead of rejecting the lower-privileged caller.

## Security conclusion

The caller remained authenticated in a lower-privileged context while the server exposed a restricted function. The weakness therefore resulted from missing server-side function-level authorization rather than only from hidden navigation or user-interface controls.
