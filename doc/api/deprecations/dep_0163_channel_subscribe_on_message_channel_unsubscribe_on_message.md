### DEP0163: `channel.subscribe(onMessage)`, `channel.unsubscribe(onMessage)`

<!-- YAML
changes:
  - version:
    - v18.7.0
    - v16.17.0
    pr-url: https://github.com/nodejs/node/pull/42714
    description: Documentation-only deprecation.
-->

Type: Documentation-only

These methods were deprecated because they can be used in a way which does not
hold the channel reference alive long enough to receive the events.

Use [`diagnostics_channel.subscribe(name, onMessage)`][] or
[`diagnostics_channel.unsubscribe(name, onMessage)`][] which does the same
thing instead.
