#### `await` keyword

Support for the `await` keyword is enabled at the top level.

```console
> await Promise.resolve(123)
123
> await Promise.reject(new Error('REPL await'))
Uncaught Error: REPL await
    at REPL2:1:54
> const timeout = util.promisify(setTimeout);
undefined
> const old = Date.now(); await timeout(1000); console.log(Date.now() - old);
1002
undefined
```

One known limitation of using the `await` keyword in the REPL is that
it will invalidate the lexical scoping of the `const` and `let`
keywords.

For example:

```console
> const m = await Promise.resolve(123)
undefined
> m
123
> const m = await Promise.resolve(234)
undefined
> m
234
```

[`--no-experimental-repl-await`][] shall disable top-level await in REPL.
