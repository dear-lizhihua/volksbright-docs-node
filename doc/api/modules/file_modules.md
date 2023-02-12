## File modules

<!--type=misc-->

If the exact filename is not found, then Node.js will attempt to load the
required filename with the added extensions: `.js`, `.json`, and finally
`.node`. When loading a file that has a different extension (e.g. `.cjs`), its
full name must be passed to `require()`, including its file extension (e.g.
`require('./file.cjs')`).

`.json` files are parsed as JSON text files, `.node` files are interpreted as
compiled addon modules loaded with `process.dlopen()`. Files using any other
extension (or no extension at all) are parsed as JavaScript text files. Refer to
the [Determining module system][] section to understand what parse goal will be
used.

A required module prefixed with `'/'` is an absolute path to the file. For
example, `require('/home/marco/foo.js')` will load the file at
`/home/marco/foo.js`.

A required module prefixed with `'./'` is relative to the file calling
`require()`. That is, `circle.js` must be in the same directory as `foo.js` for
`require('./circle')` to find it.

Without a leading `'/'`, `'./'`, or `'../'` to indicate a file, the module must
either be a core module or is loaded from a `node_modules` folder.

If the given path does not exist, `require()` will throw a
[`MODULE_NOT_FOUND`][] error.
