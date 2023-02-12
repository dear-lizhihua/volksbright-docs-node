## Class: `TestsStream`

<!-- YAML
added:
  - v18.9.0
  - v16.19.0
-->

* Extends {ReadableStream}

A successful call to [`run()`][] method will return a new {TestsStream}
object, streaming a series of events representing the execution of the tests.
`TestsStream` will emit events, in the order of the tests definition
