## `assert.doesNotMatch(string, regexp[, message])`

<!-- YAML
added:
  - v13.6.0
  - v12.16.0
changes:
  - version: v16.0.0
    pr-url: https://github.com/nodejs/node/pull/38111
    description: This API is no longer experimental.
-->

* `string` {string}
* `regexp` {RegExp}
* `message` {string|Error}

Expects the `string` input not to match the regular expression.

```mjs
import assert from 'node:assert/strict';

assert.doesNotMatch('I will fail', /fail/);
// AssertionError [ERR_ASSERTION]: The input was expected to not match the ...

assert.doesNotMatch(123, /pass/);
// AssertionError [ERR_ASSERTION]: The "string" argument must be of type string.

assert.doesNotMatch('I will pass', /different/);
// OK
```

```cjs
const assert = require('node:assert/strict');

assert.doesNotMatch('I will fail', /fail/);
// AssertionError [ERR_ASSERTION]: The input was expected to not match the ...

assert.doesNotMatch(123, /pass/);
// AssertionError [ERR_ASSERTION]: The "string" argument must be of type string.

assert.doesNotMatch('I will pass', /different/);
// OK
```

If the values do match, or if the `string` argument is of another type than
`string`, an [`AssertionError`][] is thrown with a `message` property set equal
to the value of the `message` parameter. If the `message` parameter is
undefined, a default error message is assigned. If the `message` parameter is an
instance of an [`Error`][] then it will be thrown instead of the
[`AssertionError`][].
