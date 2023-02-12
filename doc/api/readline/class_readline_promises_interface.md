### Class: `readlinePromises.Interface`

<!-- YAML
added: v17.0.0
-->

* Extends: {readline.InterfaceConstructor}

Instances of the `readlinePromises.Interface` class are constructed using the
`readlinePromises.createInterface()` method. Every instance is associated with a
single `input` [Readable][] stream and a single `output` [Writable][] stream.
The `output` stream is used to print prompts for user input that arrives on,
and is read from, the `input` stream.
