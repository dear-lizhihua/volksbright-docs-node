### `x509.infoAccess`

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

A textual representation of the certificate's authority information access
extension.

This is a line feed separated list of access descriptions. Each line begins with
the access method and the kind of the access location, followed by a colon and
the value associated with the access location.

After the prefix denoting the access method and the kind of the access location,
the remainder of each line might be enclosed in quotes to indicate that the
value is a JSON string literal. For backward compatibility, Node.js only uses
JSON string literals within this property when necessary to avoid ambiguity.
Third-party code should be prepared to handle both possible entry formats.
