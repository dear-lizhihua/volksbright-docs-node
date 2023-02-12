### `writeStream.hasColors([count][, env])`

<!-- YAML
added:
 - v11.13.0
 - v10.16.0
-->

* `count` {integer} The number of colors that are requested (minimum 2).
  **Default:** 16.
* `env` {Object} An object containing the environment variables to check. This
  enables simulating the usage of a specific terminal. **Default:**
  `process.env`.
* Returns: {boolean}

Returns `true` if the `writeStream` supports at least as many colors as provided
in `count`. Minimum support is 2 (black and white).

This has the same false positives and negatives as described in
[`writeStream.getColorDepth()`][].

```js
process.stdout.hasColors();
// Returns true or false depending on if `stdout` supports at least 16 colors.
process.stdout.hasColors(256);
// Returns true or false depending on if `stdout` supports at least 256 colors.
process.stdout.hasColors({ TMUX: '1' });
// Returns true.
process.stdout.hasColors(2 ** 24, { TMUX: '1' });
// Returns false (the environment setting pretends to support 2 ** 8 colors).
```
