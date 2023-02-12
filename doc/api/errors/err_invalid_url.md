### `ERR_INVALID_URL`

An invalid URL was passed to the [WHATWG][WHATWG URL API] [`URL`
constructor][`new URL(input)`] or the legacy [`url.parse()`][] to be parsed.
The thrown error object typically has an additional property `'input'` that
contains the URL that failed to parse.

<a id="ERR_INVALID_URL_SCHEME"></a>
