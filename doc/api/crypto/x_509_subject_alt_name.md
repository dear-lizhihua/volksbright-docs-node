### `x509.subjectAltName`

<!-- YAML
added: v15.6.0
changes:
  - version:
      - v17.3.1
      - v16.13.2
    pr-url: https://github.com/nodejs-private/node-private/pull/300
    description: Parts of this string may be encoded as JSON string literals
                 in response to CVE-2021-44532.
-->

* Type: {string}

The subject alternative name specified for this certificate.

This is a comma-separated list of subject alternative names. Each entry begins
with a string identifying the kind of the subject alternative name followed by
a colon and the value associated with the entry.

Earlier versions of Node.js incorrectly assumed that it is safe to split this
property at the two-character sequence `', '` (see [CVE-2021-44532][]). However,
both malicious and legitimate certificates can contain subject alternative names
that include this sequence when represented as a string.

After the prefix denoting the type of the entry, the remainder of each entry
might be enclosed in quotes to indicate that the value is a JSON string literal.
For backward compatibility, Node.js only uses JSON string literals within this
property when necessary to avoid ambiguity. Third-party code should be prepared
to handle both possible entry formats.
