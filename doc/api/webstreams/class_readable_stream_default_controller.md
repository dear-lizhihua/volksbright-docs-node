### Class: `ReadableStreamDefaultController`

<!-- YAML
added: v16.5.0
-->

Every {ReadableStream} has a controller that is responsible for
the internal state and management of the stream's queue. The
`ReadableStreamDefaultController` is the default controller
implementation for `ReadableStream`s that are not byte-oriented.
