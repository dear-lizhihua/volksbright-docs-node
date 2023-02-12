### Customizing REPL output

By default, [`repl.REPLServer`][] instances format output using the
[`util.inspect()`][] method before writing the output to the provided `Writable`
stream (`process.stdout` by default). The `showProxy` inspection option is set
to true by default and the `colors` option is set to true depending on the
REPL's `useColors` option.

The `useColors` boolean option can be specified at construction to instruct the
default writer to use ANSI style codes to colorize the output from the
`util.inspect()` method.

If the REPL is run as standalone program, it is also possible to change the
REPL's [inspection defaults][`util.inspect()`] from inside the REPL by using the
`inspect.replDefaults` property which mirrors the `defaultOptions` from
[`util.inspect()`][].

```console
> util.inspect.replDefaults.compact = false;
false
> [1]
[
  1
]
>
```

To fully customize the output of a [`repl.REPLServer`][] instance pass in a new
function for the `writer` option on construction. The following example, for
instance, simply converts any input text to upper case:

```js
const repl = require('node:repl');

const r = repl.start({ prompt: '> ', eval: myEval, writer: myWriter });

function myEval(cmd, context, filename, callback) {
  callback(null, cmd);
}

function myWriter(output) {
  return output.toUpperCase();
}
```
