## Types of streams

There are four fundamental stream types within Node.js:

* [`Writable`][]: streams to which data can be written (for example,
  [`fs.createWriteStream()`][]).
* [`Readable`][]: streams from which data can be read (for example,
  [`fs.createReadStream()`][]).
* [`Duplex`][]: streams that are both `Readable` and `Writable` (for example,
  [`net.Socket`][]).
* [`Transform`][]: `Duplex` streams that can modify or transform the data as it
  is written and read (for example, [`zlib.createDeflate()`][]).

Additionally, this module includes the utility functions
[`stream.pipeline()`][], [`stream.finished()`][], [`stream.Readable.from()`][]
and [`stream.addAbortSignal()`][].
