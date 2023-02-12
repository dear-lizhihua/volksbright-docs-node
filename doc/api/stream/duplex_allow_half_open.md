##### `duplex.allowHalfOpen`

<!-- YAML
added: v0.9.4
-->

* {boolean}

If `false` then the stream will automatically end the writable side when the
readable side ends. Set initially by the `allowHalfOpen` constructor option,
which defaults to `true`.

This can be changed manually to change the half-open behavior of an existing
`Duplex` stream instance, but must be changed before the `'end'` event is
emitted.
