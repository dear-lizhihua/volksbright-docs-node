### `rl.write(data[, key])`

<!-- YAML
added: v0.1.98
-->

* `data` {string}
* `key` {Object}
  * `ctrl` {boolean} `true` to indicate the <kbd>Ctrl</kbd> key.
  * `meta` {boolean} `true` to indicate the <kbd>Meta</kbd> key.
  * `shift` {boolean} `true` to indicate the <kbd>Shift</kbd> key.
  * `name` {string} The name of the a key.

The `rl.write()` method will write either `data` or a key sequence identified
by `key` to the `output`. The `key` argument is supported only if `output` is
a [TTY][] text terminal. See [TTY keybindings][] for a list of key
combinations.

If `key` is specified, `data` is ignored.

When called, `rl.write()` will resume the `input` stream if it has been
paused.

If the `InterfaceConstructor` was created with `output` set to `null` or
`undefined` the `data` and `key` are not written.

```js
rl.write('Delete this!');
// Simulate Ctrl+U to delete the line written previously
rl.write(null, { ctrl: true, name: 'u' });
```

The `rl.write()` method will write the data to the `readline` `Interface`'s
`input` _as if it were provided by the user_.
