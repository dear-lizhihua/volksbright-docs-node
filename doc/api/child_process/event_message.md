### Event: `'message'`

<!-- YAML
added: v0.5.9
-->

* `message` {Object} A parsed JSON object or primitive value.
* `sendHandle` {Handle} A [`net.Socket`][] or [`net.Server`][] object, or
  undefined.

The `'message'` event is triggered when a child process uses
[`process.send()`][] to send messages.

The message goes through serialization and parsing. The resulting
message might not be the same as what is originally sent.

If the `serialization` option was set to `'advanced'` used when spawning the
child process, the `message` argument can contain data that JSON is not able
to represent.
See [Advanced serialization][] for more details.
