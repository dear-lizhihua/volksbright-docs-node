## `readline.emitKeypressEvents(stream[, interface])`

<!-- YAML
added: v0.7.7
-->

* `stream` {stream.Readable}
* `interface` {readline.InterfaceConstructor}

The `readline.emitKeypressEvents()` method causes the given [Readable][]
stream to begin emitting `'keypress'` events corresponding to received input.

Optionally, `interface` specifies a `readline.Interface` instance for which
autocompletion is disabled when copy-pasted input is detected.

If the `stream` is a [TTY][], then it must be in raw mode.

This is automatically called by any readline instance on its `input` if the
`input` is a terminal. Closing the `readline` instance does not stop
the `input` from emitting `'keypress'` events.

```js
readline.emitKeypressEvents(process.stdin);
if (process.stdin.isTTY)
  process.stdin.setRawMode(true);
```
