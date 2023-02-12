### `error.cause`

<!-- YAML
added: v16.9.0
-->

* {any}

If present, the `error.cause` property is the underlying cause of the `Error`.
It is used when catching an error and throwing a new one with a different
message or code in order to still have access to the original error.

The `error.cause` property is typically set by calling
`new Error(message, { cause })`. It is not set by the constructor if the
`cause` option is not provided.

This property allows errors to be chained. When serializing `Error` objects,
[`util.inspect()`][] recursively serializes `error.cause` if it is set.

```js
const cause = new Error('The remote HTTP server responded with a 500 status');
const symptom = new Error('The message failed to send', { cause });

console.log(symptom);
// Prints:
//   Error: The message failed to send
//       at REPL2:1:17
//       at Script.runInThisContext (node:vm:130:12)
//       ... 7 lines matching cause stack trace ...
//       at [_line] [as _line] (node:internal/readline/interface:886:18) {
//     [cause]: Error: The remote HTTP server responded with a 500 status
//         at REPL1:1:15
//         at Script.runInThisContext (node:vm:130:12)
//         at REPLServer.defaultEval (node:repl:574:29)
//         at bound (node:domain:426:15)
//         at REPLServer.runBound [as eval] (node:domain:437:12)
//         at REPLServer.onLine (node:repl:902:10)
//         at REPLServer.emit (node:events:549:35)
//         at REPLServer.emit (node:domain:482:12)
//         at [_onLine] [as _onLine] (node:internal/readline/interface:425:12)
//         at [_line] [as _line] (node:internal/readline/interface:886:18)
```
