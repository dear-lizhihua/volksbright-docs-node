### `ERR_DOMAIN_CANNOT_SET_UNCAUGHT_EXCEPTION_CAPTURE`

[`process.setUncaughtExceptionCaptureCallback()`][] could not be called
because the `node:domain` module has been loaded at an earlier point in time.

The stack trace is extended to include the point in time at which the
`node:domain` module had been loaded.

<a id="ERR_DUPLICATE_STARTUP_SNAPSHOT_MAIN_FUNCTION"></a>
