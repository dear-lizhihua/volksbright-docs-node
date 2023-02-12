### Event: `'exit'`

<!-- YAML
added: v0.7.7
-->

The `'exit'` event is emitted when the REPL is exited either by receiving the
`.exit` command as input, the user pressing <kbd>Ctrl</kbd>+<kbd>C</kbd> twice
to signal `SIGINT`,
or by pressing <kbd>Ctrl</kbd>+<kbd>D</kbd> to signal `'end'` on the input
stream. The listener
callback is invoked without any arguments.

```js
replServer.on('exit', () => {
  console.log('Received "exit" event from repl!');
  process.exit();
});
```
