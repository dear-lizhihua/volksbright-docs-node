#### Global uncaught exceptions

<!-- YAML
changes:
  - version: v12.3.0
    pr-url: https://github.com/nodejs/node/pull/27151
    description: The `'uncaughtException'` event is from now on triggered if the
                 repl is used as standalone program.
-->

The REPL uses the [`domain`][] module to catch all uncaught exceptions for that
REPL session.

This use of the [`domain`][] module in the REPL has these side effects:

* Uncaught exceptions only emit the [`'uncaughtException'`][] event in the
  standalone REPL. Adding a listener for this event in a REPL within
  another Node.js program results in [`ERR_INVALID_REPL_INPUT`][].

  ```js
  const r = repl.start();

  r.write('process.on("uncaughtException", () => console.log("Foobar"));\n');
  // Output stream includes:
  //   TypeError [ERR_INVALID_REPL_INPUT]: Listeners for `uncaughtException`
  //   cannot be used in the REPL

  r.close();
  ```

* Trying to use [`process.setUncaughtExceptionCaptureCallback()`][] throws
  an [`ERR_DOMAIN_CANNOT_SET_UNCAUGHT_EXCEPTION_CAPTURE`][] error.
