#### `sourceMap.findEntry(lineNumber, columnNumber)`

* `lineNumber` {number}
* `columnNumber` {number}
* Returns: {Object}

Given a line number and column number in the generated source file, returns
an object representing the position in the original file. The object returned
consists of the following keys:

* generatedLine: {number}
* generatedColumn: {number}
* originalSource: {string}
* originalLine: {number}
* originalColumn: {number}
* name: {string}

[CommonJS]: modules.md
[ES Modules]: esm.md
[Source map v3 format]: https://sourcemaps.info/spec.html#h.mofvlxcwqzej
[`--enable-source-maps`]: cli.md#--enable-source-maps
[`NODE_V8_COVERAGE=dir`]: cli.md#node_v8_coveragedir
[`SourceMap`]: #class-modulesourcemap
[`module`]: modules.md#the-module-object
[module wrapper]: modules.md#the-module-wrapper
[source map include directives]: https://sourcemaps.info/spec.html#h.lmz475t4mvbx
