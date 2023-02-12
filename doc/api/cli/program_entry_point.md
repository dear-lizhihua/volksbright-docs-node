## Program entry point

The program entry point is a specifier-like string. If the string is not an
absolute path, it's resolved as a relative path from the current working
directory. That path is then resolved by [CommonJS][] module loader. If no
corresponding file is found, an error is thrown.

If a file is found, its path will be passed to the [ECMAScript module loader][]
under any of the following conditions:

* The program was started with a command-line flag that forces the entry
  point to be loaded with ECMAScript module loader.
* The file has an `.mjs` extension.
* The file does not have a `.cjs` extension, and the nearest parent
  `package.json` file contains a top-level [`"type"`][] field with a value of
  `"module"`.

Otherwise, the file is loaded using the CommonJS module loader. See
[Modules loaders][] for more details.
