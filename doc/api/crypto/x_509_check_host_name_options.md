### `x509.checkHost(name[, options])`

<!-- YAML
added: v15.6.0
changes:
  - version: v18.0.0
    pr-url: https://github.com/nodejs/node/pull/41600
    description: The subject option now defaults to `'default'`.
  - version:
    - v17.5.0
    - v16.15.0
    pr-url: https://github.com/nodejs/node/pull/41569
    description: The subject option can now be set to `'default'`.
-->

* `name` {string}
* `options` {Object}
  * `subject` {string} `'default'`, `'always'`, or `'never'`.
    **Default:** `'default'`.
  * `wildcards` {boolean} **Default:** `true`.
  * `partialWildcards` {boolean} **Default:** `true`.
  * `multiLabelWildcards` {boolean} **Default:** `false`.
  * `singleLabelSubdomains` {boolean} **Default:** `false`.
* Returns: {string|undefined} Returns a subject name that matches `name`,
  or `undefined` if no subject name matches `name`.

Checks whether the certificate matches the given host name.

If the certificate matches the given host name, the matching subject name is
returned. The returned name might be an exact match (e.g., `foo.example.com`)
or it might contain wildcards (e.g., `*.example.com`). Because host name
comparisons are case-insensitive, the returned subject name might also differ
from the given `name` in capitalization.

If the `'subject'` option is undefined or set to `'default'`, the certificate
subject is only considered if the subject alternative name extension either does
not exist or does not contain any DNS names. This behavior is consistent with
[RFC 2818][] ("HTTP Over TLS").

If the `'subject'` option is set to `'always'` and if the subject alternative
name extension either does not exist or does not contain a matching DNS name,
the certificate subject is considered.

If the `'subject'` option is set to `'never'`, the certificate subject is never
considered, even if the certificate contains no subject alternative names.
