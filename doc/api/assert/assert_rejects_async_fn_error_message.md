## `assert.rejects(asyncFn[, error][, message])`

<!-- YAML
added: v10.0.0
-->

* `asyncFn` {Function|Promise}
* `error` {RegExp|Function|Object|Error}
* `message` {string}

Awaits the `asyncFn` promise or, if `asyncFn` is a function, immediately
calls the function and awaits the returned promise to complete. It will then
check that the promise is rejected.

If `asyncFn` is a function and it throws an error synchronously,
`assert.rejects()` will return a rejected `Promise` with that error. If the
function does not return a promise, `assert.rejects()` will return a rejected
`Promise` with an [`ERR_INVALID_RETURN_VALUE`][] error. In both cases the error
handler is skipped.

Besides the async nature to await the completion behaves identically to
[`assert.throws()`][].

If specified, `error` can be a [`Class`][], [`RegExp`][], a validation function,
an object where each property will be tested for, or an instance of error where
each property will be tested for including the non-enumerable `message` and
`name` properties.

If specified, `message` will be the message provided by the [`AssertionError`][]
if the `asyncFn` fails to reject.

```mjs
import assert from 'node:assert/strict';

await assert.rejects(
  async () => {
    throw new TypeError('Wrong value');
  },
  {
    name: 'TypeError',
    message: 'Wrong value',
  },
);
```

```cjs
const assert = require('node:assert/strict');

(async () => {
  await assert.rejects(
    async () => {
      throw new TypeError('Wrong value');
    },
    {
      name: 'TypeError',
      message: 'Wrong value',
    },
  );
})();
```

```mjs
import assert from 'node:assert/strict';

await assert.rejects(
  async () => {
    throw new TypeError('Wrong value');
  },
  (err) => {
    assert.strictEqual(err.name, 'TypeError');
    assert.strictEqual(err.message, 'Wrong value');
    return true;
  },
);
```

```cjs
const assert = require('node:assert/strict');

(async () => {
  await assert.rejects(
    async () => {
      throw new TypeError('Wrong value');
    },
    (err) => {
      assert.strictEqual(err.name, 'TypeError');
      assert.strictEqual(err.message, 'Wrong value');
      return true;
    },
  );
})();
```

```mjs
import assert from 'node:assert/strict';

assert.rejects(
  Promise.reject(new Error('Wrong value')),
  Error,
).then(() => {
  // ...
});
```

```cjs
const assert = require('node:assert/strict');

assert.rejects(
  Promise.reject(new Error('Wrong value')),
  Error,
).then(() => {
  // ...
});
```

`error` cannot be a string. If a string is provided as the second
argument, then `error` is assumed to be omitted and the string will be used for
`message` instead. This can lead to easy-to-miss mistakes. Please read the
example in [`assert.throws()`][] carefully if using a string as the second
argument gets considered.
