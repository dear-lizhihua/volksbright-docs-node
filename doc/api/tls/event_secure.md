### Event: `'secure'`

<!-- YAML
added: v0.3.2
deprecated: v0.11.3
-->

The `'secure'` event is emitted by the `SecurePair` object once a secure
connection has been established.

As with checking for the server
[`'secureConnection'`][]
event, `pair.cleartext.authorized` should be inspected to confirm whether the
certificate used is properly authorized.
