## Introduction

<!--name=esm-->

ECMAScript modules are [the official standard format][] to package JavaScript
code for reuse. Modules are defined using a variety of [`import`][] and
[`export`][] statements.

The following example of an ES module exports a function:

```js
// addTwo.mjs
function addTwo(num) {
  return num + 2;
}

export { addTwo };
```

The following example of an ES module imports the function from `addTwo.mjs`:

```js
// app.mjs
import { addTwo } from './addTwo.mjs';

// Prints: 6
console.log(addTwo(4));
```

Node.js fully supports ECMAScript modules as they are currently specified and
provides interoperability between them and its original module format,
[CommonJS][].

<!-- Anchors to make sure old links find a target -->

<i id="esm_package_json_type_field"></i><i id="esm_package_scope_and_file_extensions"></i><i id="esm_input_type_flag"></i>
