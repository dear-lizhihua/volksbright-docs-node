### DEP0156: `.aborted` property and `'abort'`, `'aborted'` event in `http`

<!-- YAML
changes:
  - version:
    - v17.0.0
    - v16.12.0
    pr-url: https://github.com/nodejs/node/pull/36670
    description: Documentation-only deprecation.
-->

Type: Documentation-only

Move to {Stream} API instead, as the [`http.ClientRequest`][],
[`http.ServerResponse`][], and [`http.IncomingMessage`][] are all stream-based.
Check `stream.destroyed` instead of the `.aborted` property, and listen for
`'close'` instead of `'abort'`, `'aborted'` event.

The `.aborted` property and `'abort'` event are only useful for detecting
`.abort()` calls. For closing a request early, use the Stream
`.destroy([error])` then check the `.destroyed` property and `'close'` event
should have the same effect. The receiving end should also check the
[`readable.readableEnded`][] value on [`http.IncomingMessage`][] to get whether
it was an aborted or graceful destroy.
