# F-04 Technical Validation

> Sanitized reconstruction. The original diagnostic path, runtime versions, filesystem paths, module list, and environment-specific values are intentionally not reproduced.

## Direct request

```http
GET /diagnostic-info.php HTTP/1.1
Host: app.example.test
```

```http
HTTP/1.1 200 OK
Content-Type: text/html

[runtime version and build information]
[server configuration details]
[configuration file locations]
[loaded modules and environment information]
```

## Security conclusion

A server-side diagnostic page was directly reachable from the assessed application context and exposed detailed runtime and deployment information that was not required for normal application use.
