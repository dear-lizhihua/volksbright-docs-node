### `x509.checkEmail(email[, options])`

<!-- YAML
added: v15.6.0
changes:
  - version: v18.0.0
    pr-url: https://github.com/nodejs/node/pull/41600
    description: The subject option now defaults to `'default'`.
  - version:
      - v17.5.0
      - v16.14.1
    pr-url: https://github.com/nodejs/node/pull/41599
    description: The `wildcards`, `partialWildcards`, `multiLabelWildcards`, and
                 `singleLabelSubdomains` options have been removed since they
                 had no effect.
  - version:
    - v17.5.0
    - v16.15.0
    pr-url: https://github.com/nodejs/node/pull/41569
    description: The subject option can now be set to `'default'`.
-->

* `email` {string}
* `options` {Object}
  * `subject` {string} `'default'`, `'always'`, or `'never'`.
    **Default:** `'default'`.
* Returns: {string|undefined} Returns `email` if the certificate matches,
  `undefined` if it does not.

Checks whether the certificate matches the given email address.

If the `'subject'` option is undefined or set to `'default'`, the certificate
subject is only considered if the subject alternative name extension either does
not exist or does not contain any email addresses.

If the `'subject'` option is set to `'always'` and if the subject alternative
name extension either does not exist or does not contain a matching email
address, the certificate subject is considered.

If the `'subject'` option is set to `'never'`, the certificate subject is never
considered, even if the certificate contains no subject alternative names.
