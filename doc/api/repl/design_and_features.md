## Design and features

The `node:repl` module exports the [`repl.REPLServer`][] class. While running,
instances of [`repl.REPLServer`][] will accept individual lines of user input,
evaluate those according to a user-defined evaluation function, then output the
result. Input and output may be from `stdin` and `stdout`, respectively, or may
be connected to any Node.js [stream][].

Instances of [`repl.REPLServer`][] support automatic completion of inputs,
completion preview, simplistic Emacs-style line editing, multi-line inputs,
[ZSH][]-like reverse-i-search, [ZSH][]-like substring-based history search,
ANSI-styled output, saving and restoring current REPL session state, error
recovery, and customizable evaluation functions. Terminals that do not support
ANSI styles and Emacs-style line editing automatically fall back to a limited
feature set.
