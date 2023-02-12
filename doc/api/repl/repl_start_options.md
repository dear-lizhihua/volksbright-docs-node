## `repl.start([options])`

<!-- YAML
added: v0.1.91
changes:
  - version:
     - v13.4.0
     - v12.17.0
    pr-url: https://github.com/nodejs/node/pull/30811
    description: The `preview` option is now available.
  - version: v12.0.0
    pr-url: https://github.com/nodejs/node/pull/26518
    description: The `terminal` option now follows the default description in
                 all cases and `useColors` checks `hasColors()` if available.
  - version: v10.0.0
    pr-url: https://github.com/nodejs/node/pull/19187
    description: The `REPL_MAGIC_MODE` `replMode` was removed.
  - version: v6.3.0
    pr-url: https://github.com/nodejs/node/pull/6635
    description: The `breakEvalOnSigint` option is supported now.
  - version: v5.8.0
    pr-url: https://github.com/nodejs/node/pull/5388
    description: The `options` parameter is optional now.
-->

* `options` {Object|string}
  * `prompt` {string} The input prompt to display. **Default:** `'> '`
    (with a trailing space).
  * `input` {stream.Readable} The `Readable` stream from which REPL input will
    be read. **Default:** `process.stdin`.
  * `output` {stream.Writable} The `Writable` stream to which REPL output will
    be written. **Default:** `process.stdout`.
  * `terminal` {boolean} If `true`, specifies that the `output` should be
    treated as a TTY terminal.
    **Default:** checking the value of the `isTTY` property on the `output`
    stream upon instantiation.
  * `eval` {Function} The function to be used when evaluating each given line
    of input. **Default:** an async wrapper for the JavaScript `eval()`
    function. An `eval` function can error with `repl.Recoverable` to indicate
    the input was incomplete and prompt for additional lines.
  * `useColors` {boolean} If `true`, specifies that the default `writer`
    function should include ANSI color styling to REPL output. If a custom
    `writer` function is provided then this has no effect. **Default:** checking
    color support on the `output` stream if the REPL instance's `terminal` value
    is `true`.
  * `useGlobal` {boolean} If `true`, specifies that the default evaluation
    function will use the JavaScript `global` as the context as opposed to
    creating a new separate context for the REPL instance. The node CLI REPL
    sets this value to `true`. **Default:** `false`.
  * `ignoreUndefined` {boolean} If `true`, specifies that the default writer
    will not output the return value of a command if it evaluates to
    `undefined`. **Default:** `false`.
  * `writer` {Function} The function to invoke to format the output of each
    command before writing to `output`. **Default:** [`util.inspect()`][].
  * `completer` {Function} An optional function used for custom Tab auto
    completion. See [`readline.InterfaceCompleter`][] for an example.
  * `replMode` {symbol} A flag that specifies whether the default evaluator
    executes all JavaScript commands in strict mode or default (sloppy) mode.
    Acceptable values are:
    * `repl.REPL_MODE_SLOPPY` to evaluate expressions in sloppy mode.
    * `repl.REPL_MODE_STRICT` to evaluate expressions in strict mode. This is
      equivalent to prefacing every repl statement with `'use strict'`.
  * `breakEvalOnSigint` {boolean} Stop evaluating the current piece of code when
    `SIGINT` is received, such as when <kbd>Ctrl</kbd>+<kbd>C</kbd> is pressed.
    This cannot be used
    together with a custom `eval` function. **Default:** `false`.
  * `preview` {boolean} Defines if the repl prints autocomplete and output
    previews or not. **Default:** `true` with the default eval function and
    `false` in case a custom eval function is used. If `terminal` is falsy, then
    there are no previews and the value of `preview` has no effect.
* Returns: {repl.REPLServer}

The `repl.start()` method creates and starts a [`repl.REPLServer`][] instance.

If `options` is a string, then it specifies the input prompt:

```js
const repl = require('node:repl');

// a Unix style prompt
repl.start('$ ');
```
