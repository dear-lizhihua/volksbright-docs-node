# This binary contains the result of the execution of entry.js
$ out/Release/node
```

In the example above, `entry.js` can use methods from the `v8.startupSnapshot`
interface to specify how to save information for custom objects in the snapshot
during serialization and how the information can be used to synchronize these
objects during deserialization of the snapshot. For example, if the `entry.js`
contains the following script:

```cjs
'use strict';

const fs = require('node:fs');
const zlib = require('node:zlib');
const path = require('node:path');
const assert = require('node:assert');

const {
  isBuildingSnapshot,
  addSerializeCallback,
  addDeserializeCallback,
  setDeserializeMainFunction,
} = require('node:v8').startupSnapshot;

const filePath = path.resolve(__dirname, '../x1024.txt');
const storage = {};

assert(isBuildingSnapshot());

addSerializeCallback(({ filePath }) => {
  storage[filePath] = zlib.gzipSync(fs.readFileSync(filePath));
}, { filePath });

addDeserializeCallback(({ filePath }) => {
  storage[filePath] = zlib.gunzipSync(storage[filePath]);
}, { filePath });

setDeserializeMainFunction(({ filePath }) => {
  console.log(storage[filePath].toString());
}, { filePath });
```

The resulted binary will simply print the data deserialized from the snapshot
during start up:

```console
$ out/Release/node