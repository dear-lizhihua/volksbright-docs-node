### `stream.compose(...streams)`

<!-- YAML
added: v16.9.0
-->

> Stability: 1 - `stream.compose` is experimental.

* `streams` {Stream\[]|Iterable\[]|AsyncIterable\[]|Function\[]}
* Returns: {stream.Duplex}

Combines two or more streams into a `Duplex` stream that writes to the
first stream and reads from the last. Each provided stream is piped into
the next, using `stream.pipeline`. If any of the streams error then all
are destroyed, including the outer `Duplex` stream.

Because `stream.compose` returns a new stream that in turn can (and
should) be piped into other streams, it enables composition. In contrast,
when passing streams to `stream.pipeline`, typically the first stream is
a readable stream and the last a writable stream, forming a closed
circuit.

If passed a `Function` it must be a factory method taking a `source`
`Iterable`.

```mjs
import { compose, Transform } from 'node:stream';

const removeSpaces = new Transform({
  transform(chunk, encoding, callback) {
    callback(null, String(chunk).replace(' ', ''));
  },
});

async function* toUpper(source) {
  for await (const chunk of source) {
    yield String(chunk).toUpperCase();
  }
}

let res = '';
for await (const buf of compose(removeSpaces, toUpper).end('hello world')) {
  res += buf;
}

console.log(res); // prints 'HELLOWORLD'
```

`stream.compose` can be used to convert async iterables, generators and
functions into streams.

* `AsyncIterable` converts into a readable `Duplex`. Cannot yield
  `null`.
* `AsyncGeneratorFunction` converts into a readable/writable transform `Duplex`.
  Must take a source `AsyncIterable` as first parameter. Cannot yield
  `null`.
* `AsyncFunction` converts into a writable `Duplex`. Must return
  either `null` or `undefined`.

```mjs
import { compose } from 'node:stream';
import { finished } from 'node:stream/promises';

// Convert AsyncIterable into readable Duplex.
const s1 = compose(async function*() {
  yield 'Hello';
  yield 'World';
}());

// Convert AsyncGenerator into transform Duplex.
const s2 = compose(async function*(source) {
  for await (const chunk of source) {
    yield String(chunk).toUpperCase();
  }
});

let res = '';

// Convert AsyncFunction into writable Duplex.
const s3 = compose(async function(source) {
  for await (const chunk of source) {
    res += chunk;
  }
});

await finished(compose(s1, s2, s3));

console.log(res); // prints 'HELLOWORLD'
```

See [`readable.compose(stream)`][] for `stream.compose` as operator.
