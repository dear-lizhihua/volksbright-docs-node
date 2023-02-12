### Customizing ESM specifier resolution algorithm

The [Loaders API][] provides a mechanism for customizing the ESM specifier
resolution algorithm. An example loader that provides CommonJS-style resolution
for ESM specifiers is [commonjs-extension-resolution-loader][].

<!-- Note: The cjs-module-lexer link should be kept in-sync with the deps version -->

[6.1.7 Array Index]: https://tc39.es/ecma262/#integer-index
[Addons]: addons.md
[CommonJS]: modules.md
[Conditional exports]: packages.md#conditional-exports
[Core modules]: modules.md#core-modules
[Determining module system]: packages.md#determining-module-system
[Dynamic `import()`]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/import
[ES Module Integration Proposal for WebAssembly]: https://github.com/webassembly/esm-integration
[HTTPS and HTTP imports]: #https-and-http-imports
[Import Assertions]: #import-assertions
[Import Assertions proposal]: https://github.com/tc39/proposal-import-assertions
[JSON modules]: #json-modules
[Loaders API]: #loaders
[Node.js Module Resolution Algorithm]: #resolver-algorithm-specification
[Terminology]: #terminology
[URL]: https://url.spec.whatwg.org/
[`"exports"`]: packages.md#exports
[`"type"`]: packages.md#type
[`--input-type`]: cli.md#--input-typetype
[`ArrayBuffer`]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/ArrayBuffer
[`SharedArrayBuffer`]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/SharedArrayBuffer
[`TypedArray`]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/TypedArray
[`Uint8Array`]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Uint8Array
[`data:` URLs]: https://developer.mozilla.org/en-US/docs/Web/HTTP/Basics_of_HTTP/Data_URIs
[`export`]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/export
[`import()`]: #import-expressions
[`import.meta.resolve`]: #importmetaresolvespecifier-parent
[`import.meta.url`]: #importmetaurl
[`import`]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/import
[`module.createRequire()`]: module.md#modulecreaterequirefilename
[`module.syncBuiltinESMExports()`]: module.md#modulesyncbuiltinesmexports
[`package.json`]: packages.md#nodejs-packagejson-field-definitions
[`port.ref()`]: https://nodejs.org/dist/latest-v17.x/docs/api/worker_threads.html#portref
[`port.unref()`]: https://nodejs.org/dist/latest-v17.x/docs/api/worker_threads.html#portunref
[`process.dlopen`]: process.md#processdlopenmodule-filename-flags
[`string`]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String
[`util.TextDecoder`]: util.md#class-utiltextdecoder
[cjs-module-lexer]: https://github.com/nodejs/cjs-module-lexer/tree/1.2.2
[commonjs-extension-resolution-loader]: https://github.com/nodejs/loaders-test/tree/main/commonjs-extension-resolution-loader
[custom https loader]: #https-loader
[load hook]: #loadurl-context-nextload
[percent-encoded]: url.md#percent-encoding-in-urls
[resolve hook]: #resolvespecifier-context-nextresolve
[special scheme]: https://url.spec.whatwg.org/#special-scheme
[status code]: process.md#exit-codes
[the official standard format]: https://tc39.github.io/ecma262/#sec-modules
[url.pathToFileURL]: url.md#urlpathtofileurlpath
