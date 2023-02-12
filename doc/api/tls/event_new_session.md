### Event: `'newSession'`

<!-- YAML
added: v0.9.2
changes:
  - version: v0.11.12
    pr-url: https://github.com/nodejs/node-v0.x-archive/pull/7118
    description: The `callback` argument is now supported.
-->

The `'newSession'` event is emitted upon creation of a new TLS session. This may
be used to store sessions in external storage. The data should be provided to
the [`'resumeSession'`][] callback.

The listener callback is passed three arguments when called:

* `sessionId` {Buffer} The TLS session identifier
* `sessionData` {Buffer} The TLS session data
* `callback` {Function} A callback function taking no arguments that must be
  invoked in order for data to be sent or received over the secure connection.

Listening for this event will have an effect only on connections established
after the addition of the event listener.
