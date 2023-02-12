### Event: `'close'`

<!-- YAML
added: v0.1.98
-->

The `'close'` event is emitted when one of the following occur:

* The `rl.close()` method is called and the `InterfaceConstructor` instance has
  relinquished control over the `input` and `output` streams;
* The `input` stream receives its `'end'` event;
* The `input` stream receives <kbd>Ctrl</kbd>+<kbd>D</kbd> to signal
  end-of-transmission (EOT);
* The `input` stream receives <kbd>Ctrl</kbd>+<kbd>C</kbd> to signal `SIGINT`
  and there is no `'SIGINT'` event listener registered on the
  `InterfaceConstructor` instance.

The listener function is called without passing any arguments.

The `InterfaceConstructor` instance is finished once the `'close'` event is
emitted.
