### ECMAScript modules loader entry point caveat

When loading [ECMAScript module loader][] loads the program entry point, the `node`
command will only accept as input only files with `.js`, `.mjs`, or `.cjs`
extensions; and with `.wasm` extensions when
[`--experimental-wasm-modules`][] is enabled.
