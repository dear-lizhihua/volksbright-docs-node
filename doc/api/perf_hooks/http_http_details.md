### HTTP ('http') Details

When `performanceEntry.type` is equal to `'http'`, the
`performanceNodeEntry.detail` property will be an {Object} containing
additional information.

If `performanceEntry.name` is equal to `HttpClient`, the `detail`
will contain the following properties: `req`, `res`. And the `req` property
will be an {Object} containing `method`, `url`, `headers`, the `res` property
will be an {Object} containing `statusCode`, `statusMessage`, `headers`.

If `performanceEntry.name` is equal to `HttpRequest`, the `detail`
will contain the following properties: `req`, `res`. And the `req` property
will be an {Object} containing `method`, `url`, `headers`, the `res` property
will be an {Object} containing `statusCode`, `statusMessage`, `headers`.

This could add additional memory overhead and should only be used for
diagnostic purposes, not left turned on in production by default.
