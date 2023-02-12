### Perfect forward secrecy

<!-- type=misc -->

The term _[forward secrecy][]_ or _perfect forward secrecy_ describes a feature
of key-agreement (i.e., key-exchange) methods. That is, the server and client
keys are used to negotiate new temporary keys that are used specifically and
only for the current communication session. Practically, this means that even
if the server's private key is compromised, communication can only be decrypted
by eavesdroppers if the attacker manages to obtain the key-pair specifically
generated for the session.

Perfect forward secrecy is achieved by randomly generating a key pair for
key-agreement on every TLS/SSL handshake (in contrast to using the same key for
all sessions). Methods implementing this technique are called "ephemeral".

Currently two methods are commonly used to achieve perfect forward secrecy (note
the character "E" appended to the traditional abbreviations):

* [DHE][]: An ephemeral version of the Diffie-Hellman key-agreement protocol.
* [ECDHE][]: An ephemeral version of the Elliptic Curve Diffie-Hellman
  key-agreement protocol.

To use perfect forward secrecy using `DHE` with the `node:tls` module, it is
required to generate Diffie-Hellman parameters and specify them with the
`dhparam` option to [`tls.createSecureContext()`][]. The following illustrates
the use of the OpenSSL command-line interface to generate such parameters:

```bash
openssl dhparam -outform PEM -out dhparam.pem 2048
```

If using perfect forward secrecy using `ECDHE`, Diffie-Hellman parameters are
not required and a default ECDHE curve will be used. The `ecdhCurve` property
can be used when creating a TLS Server to specify the list of names of supported
curves to use, see [`tls.createServer()`][] for more info.

Perfect forward secrecy was optional up to TLSv1.2. As of TLSv1.3, (EC)DHE is
always used (with the exception of PSK-only connections).
