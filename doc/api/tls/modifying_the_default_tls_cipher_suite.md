## Modifying the default TLS cipher suite

Node.js is built with a default suite of enabled and disabled TLS ciphers. This
default cipher list can be configured when building Node.js to allow
distributions to provide their own default list.

The following command can be used to show the default cipher suite:

```console
node -p crypto.constants.defaultCoreCipherList | tr ':' '\n'
TLS_AES_256_GCM_SHA384
TLS_CHACHA20_POLY1305_SHA256
TLS_AES_128_GCM_SHA256
ECDHE-RSA-AES128-GCM-SHA256
ECDHE-ECDSA-AES128-GCM-SHA256
ECDHE-RSA-AES256-GCM-SHA384
ECDHE-ECDSA-AES256-GCM-SHA384
DHE-RSA-AES128-GCM-SHA256
ECDHE-RSA-AES128-SHA256
DHE-RSA-AES128-SHA256
ECDHE-RSA-AES256-SHA384
DHE-RSA-AES256-SHA384
ECDHE-RSA-AES256-SHA256
DHE-RSA-AES256-SHA256
HIGH
!aNULL
!eNULL
!EXPORT
!DES
!RC4
!MD5
!PSK
!SRP
!CAMELLIA
```

This default can be replaced entirely using the [`--tls-cipher-list`][]
command-line switch (directly, or via the [`NODE_OPTIONS`][] environment
variable). For instance, the following makes `ECDHE-RSA-AES128-GCM-SHA256:!RC4`
the default TLS cipher suite:

```bash
node --tls-cipher-list='ECDHE-RSA-AES128-GCM-SHA256:!RC4' server.js

export NODE_OPTIONS=--tls-cipher-list='ECDHE-RSA-AES128-GCM-SHA256:!RC4'
node server.js
```

The default can also be replaced on a per client or server basis using the
`ciphers` option from [`tls.createSecureContext()`][], which is also available
in [`tls.createServer()`][], [`tls.connect()`][], and when creating new
[`tls.TLSSocket`][]s.

The ciphers list can contain a mixture of TLSv1.3 cipher suite names, the ones
that start with `'TLS_'`, and specifications for TLSv1.2 and below cipher
suites. The TLSv1.2 ciphers support a legacy specification format, consult
the OpenSSL [cipher list format][] documentation for details, but those
specifications do _not_ apply to TLSv1.3 ciphers. The TLSv1.3 suites can only
be enabled by including their full name in the cipher list. They cannot, for
example, be enabled or disabled by using the legacy TLSv1.2 `'EECDH'` or
`'!EECDH'` specification.

Despite the relative order of TLSv1.3 and TLSv1.2 cipher suites, the TLSv1.3
protocol is significantly more secure than TLSv1.2, and will always be chosen
over TLSv1.2 if the handshake indicates it is supported, and if any TLSv1.3
cipher suites are enabled.

The default cipher suite included within Node.js has been carefully
selected to reflect current security best practices and risk mitigation.
Changing the default cipher suite can have a significant impact on the security
of an application. The `--tls-cipher-list` switch and `ciphers` option should by
used only if absolutely necessary.

The default cipher suite prefers GCM ciphers for [Chrome's 'modern
cryptography' setting][] and also prefers ECDHE and DHE ciphers for perfect
forward secrecy, while offering _some_ backward compatibility.

Old clients that rely on insecure and deprecated RC4 or DES-based ciphers
(like Internet Explorer 6) cannot complete the handshaking process with
the default configuration. If these clients _must_ be supported, the
[TLS recommendations][] may offer a compatible cipher suite. For more details
on the format, see the OpenSSL [cipher list format][] documentation.

There are only five TLSv1.3 cipher suites:

* `'TLS_AES_256_GCM_SHA384'`
* `'TLS_CHACHA20_POLY1305_SHA256'`
* `'TLS_AES_128_GCM_SHA256'`
* `'TLS_AES_128_CCM_SHA256'`
* `'TLS_AES_128_CCM_8_SHA256'`

The first three are enabled by default. The two `CCM`-based suites are supported
by TLSv1.3 because they may be more performant on constrained systems, but they
are not enabled by default since they offer less security.
