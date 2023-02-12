## `path.basename(path[, suffix])`

<!-- YAML
added: v0.1.25
changes:
  - version: v6.0.0
    pr-url: https://github.com/nodejs/node/pull/5348
    description: Passing a non-string as the `path` argument will throw now.
-->

* `path` {string}
* `suffix` {string} An optional suffix to remove
* Returns: {string}

The `path.basename()` method returns the last portion of a `path`, similar to
the Unix `basename` command. Trailing [directory separators][`path.sep`] are
ignored.

```js
path.basename('/foo/bar/baz/asdf/quux.html');
// Returns: 'quux.html'

path.basename('/foo/bar/baz/asdf/quux.html', '.html');
// Returns: 'quux'
```

Although Windows usually treats file names, including file extensions, in a
case-insensitive manner, this function does not. For example, `C:\\foo.html` and
`C:\\foo.HTML` refer to the same file, but `basename` treats the extension as a
case-sensitive string:

```js
path.win32.basename('C:\\foo.html', '.html');
// Returns: 'foo'

path.win32.basename('C:\\foo.HTML', '.html');
// Returns: 'foo.HTML'
```

A [`TypeError`][] is thrown if `path` is not a string or if `suffix` is given
and is not a string.
