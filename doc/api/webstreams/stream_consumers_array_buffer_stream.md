#### `streamConsumers.arrayBuffer(stream)`

<!-- YAML
added: v16.7.0
-->

* `stream` {ReadableStream|stream.Readable|AsyncIterator}
* Returns: {Promise} Fulfills with an `ArrayBuffer` containing the full
  contents of the stream.

```mjs
import { buffer as arrayBuffer } from 'node:stream/consumers';
import { Readable } from 'node:stream';
import { TextEncoder } from 'node:util';

const encoder = new TextEncoder();
const dataArray = encoder.encode('hello world from consumers!');

const readable = Readable.from(dataArray);
const data = await arrayBuffer(readable);
console.log(`from readable: ${data.byteLength}`);
```

```cjs
const { arrayBuffer } = require('node:stream/consumers');
const { Readable } = require('node:stream');
const { TextEncoder } = require('node:util');

const encoder = new TextEncoder();
const dataArray = encoder.encode('hello world from consumers!');
const readable = Readable.from(dataArray);
arrayBuffer(readable).then((data) => {
  console.log(`from readable: ${data.byteLength}`);
});
```
