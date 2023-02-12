### Class: `ReadableByteStreamController`

<!-- YAML
added: v16.5.0
changes:
  - version: v18.10.0
    pr-url: https://github.com/nodejs/node/pull/44702
    description: Support handling a BYOB pull request from a released reader.
-->

Every {ReadableStream} has a controller that is responsible for
the internal state and management of the stream's queue. The
`ReadableByteStreamController` is for byte-oriented `ReadableStream`s.
