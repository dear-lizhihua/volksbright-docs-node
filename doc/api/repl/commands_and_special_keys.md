### Commands and special keys

The following special commands are supported by all REPL instances:

* `.break`: When in the process of inputting a multi-line expression, enter
  the `.break` command (or press <kbd>Ctrl</kbd>+<kbd>C</kbd>) to abort
  further input or processing of that expression.
* `.clear`: Resets the REPL `context` to an empty object and clears any
  multi-line expression being input.
* `.exit`: Close the I/O stream, causing the REPL to exit.
* `.help`: Show this list of special commands.
* `.save`: Save the current REPL session to a file:
  `> .save ./file/to/save.js`
* `.load`: Load a file into the current REPL session.
  `> .load ./file/to/load.js`
* `.editor`: Enter editor mode (<kbd>Ctrl</kbd>+<kbd>D</kbd> to
  finish, <kbd>Ctrl</kbd>+<kbd>C</kbd> to cancel).

```console
> .editor
// Entering editor mode (^D to finish, ^C to cancel)
function welcome(name) {
  return `Hello ${name}!`;
}

welcome('Node.js User');

// ^D
'Hello Node.js User!'
>
```

The following key combinations in the REPL have these special effects:

* <kbd>Ctrl</kbd>+<kbd>C</kbd>: When pressed once, has the same effect as the
  `.break` command.
  When pressed twice on a blank line, has the same effect as the `.exit`
  command.
* <kbd>Ctrl</kbd>+<kbd>D</kbd>: Has the same effect as the `.exit` command.
* <kbd>Tab</kbd>: When pressed on a blank line, displays global and local
  (scope) variables. When pressed while entering other input, displays relevant
  autocompletion options.

For key bindings related to the reverse-i-search, see [`reverse-i-search`][].
For all other key bindings, see [TTY keybindings][].
