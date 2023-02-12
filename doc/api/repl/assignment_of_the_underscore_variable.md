#### Assignment of the `_` (underscore) variable

<!-- YAML
changes:
  - version: v9.8.0
    pr-url: https://github.com/nodejs/node/pull/18919
    description: Added `_error` support.
-->

The default evaluator will, by default, assign the result of the most recently
evaluated expression to the special variable `_` (underscore).
Explicitly setting `_` to a value will disable this behavior.

```console
> [ 'a', 'b', 'c' ]
[ 'a', 'b', 'c' ]
> _.length
3
> _ += 1
Expression assignment to _ now disabled.
4
> 1 + 1
2
> _
4
```

Similarly, `_error` will refer to the last seen error, if there was any.
Explicitly setting `_error` to a value will disable this behavior.

```console
> throw new Error('foo');
Uncaught Error: foo
> _error.message
'foo'
```
