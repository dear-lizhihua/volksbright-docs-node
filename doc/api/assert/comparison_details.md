### Comparison details

* Primitive values are compared with the [`==` operator][],
  with the exception of `NaN`. It is treated as being identical in case
  both sides are `NaN`.
* [Type tags][Object.prototype.toString()] of objects should be the same.
* Only [enumerable "own" properties][] are considered.
* [`Error`][] names and messages are always compared, even if these are not
  enumerable properties.
* [Object wrappers][] are compared both as objects and unwrapped values.
* `Object` properties are compared unordered.
* [`Map`][] keys and [`Set`][] items are compared unordered.
* Recursion stops when both sides differ or both sides encounter a circular
  reference.
* Implementation does not test the [`[[Prototype]]`][prototype-spec] of
  objects.
* [`Symbol`][] properties are not compared.
* [`WeakMap`][] and [`WeakSet`][] comparison does not rely on their values.
* [`RegExp`][] lastIndex, flags, and source are always compared, even if these
  are not enumerable properties.

The following example does not throw an [`AssertionError`][] because the
primitives are compared using the [`==` operator][].

```mjs
import assert from 'node:assert';
// WARNING: This does not throw an AssertionError!

assert.deepEqual('+00000000', false);
```

```cjs
const assert = require('node:assert');
// WARNING: This does not throw an AssertionError!

assert.deepEqual('+00000000', false);
```

"Deep" equality means that the enumerable "own" properties of child objects
are evaluated also:

```mjs
import assert from 'node:assert';

const obj1 = {
  a: {
    b: 1,
  },
};
const obj2 = {
  a: {
    b: 2,
  },
};
const obj3 = {
  a: {
    b: 1,
  },
};
const obj4 = { __proto__: obj1 };

assert.deepEqual(obj1, obj1);
// OK

// Values of b are different:
assert.deepEqual(obj1, obj2);
// AssertionError: { a: { b: 1 } } deepEqual { a: { b: 2 } }

assert.deepEqual(obj1, obj3);
// OK

// Prototypes are ignored:
assert.deepEqual(obj1, obj4);
// AssertionError: { a: { b: 1 } } deepEqual {}
```

```cjs
const assert = require('node:assert');

const obj1 = {
  a: {
    b: 1,
  },
};
const obj2 = {
  a: {
    b: 2,
  },
};
const obj3 = {
  a: {
    b: 1,
  },
};
const obj4 = { __proto__: obj1 };

assert.deepEqual(obj1, obj1);
// OK

// Values of b are different:
assert.deepEqual(obj1, obj2);
// AssertionError: { a: { b: 1 } } deepEqual { a: { b: 2 } }

assert.deepEqual(obj1, obj3);
// OK

// Prototypes are ignored:
assert.deepEqual(obj1, obj4);
// AssertionError: { a: { b: 1 } } deepEqual {}
```

If the values are not equal, an [`AssertionError`][] is thrown with a `message`
property set equal to the value of the `message` parameter. If the `message`
parameter is undefined, a default error message is assigned. If the `message`
parameter is an instance of an [`Error`][] then it will be thrown instead of the
[`AssertionError`][].
