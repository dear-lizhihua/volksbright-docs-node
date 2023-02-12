#### Recoverable errors

At the REPL prompt, pressing <kbd>Enter</kbd> sends the current line of input to
the `eval` function. In order to support multi-line input, the `eval` function
can return an instance of `repl.Recoverable` to the provided callback function:

```js
function myEval(cmd, context, filename, callback) {
  let result;
  try {
    result = vm.runInThisContext(cmd);
  } catch (e) {
    if (isRecoverableError(e)) {
      return callback(new repl.Recoverable(e));
    }
  }
  callback(null, result);
}

function isRecoverableError(error) {
  if (error.name === 'SyntaxError') {
    return /^(Unexpected end of input|Unexpected token)/.test(error.message);
  }
  return false;
}
```
