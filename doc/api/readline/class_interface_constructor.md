## Class: `InterfaceConstructor`

<!-- YAML
added: v0.1.104
-->

* Extends: {EventEmitter}

Instances of the `InterfaceConstructor` class are constructed using the
`readlinePromises.createInterface()` or `readline.createInterface()` method.
Every instance is associated with a single `input` [Readable][] stream and a
single `output` [Writable][] stream.
The `output` stream is used to print prompts for user input that arrives on,
and is read from, the `input` stream.
