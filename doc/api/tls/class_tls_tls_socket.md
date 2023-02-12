## Class: `tls.TLSSocket`

<!-- YAML
added: v0.11.4
-->

* Extends: {net.Socket}

Performs transparent encryption of written data and all required TLS
negotiation.

Instances of `tls.TLSSocket` implement the duplex [Stream][] interface.

Methods that return TLS connection metadata (e.g.
[`tls.TLSSocket.getPeerCertificate()`][]) will only return data while the
connection is open.
