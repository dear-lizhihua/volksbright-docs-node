# Diagnostics Channel

<!-- YAML
added: v15.1.0
changes:
  - version:
      - v19.2.0
      - v18.13.0
    pr-url: https://github.com/nodejs/node/pull/45290
    description: diagnostics_channel is now Stable.
-->

<!--introduced_in=v15.1.0-->

> Stability: 2 - Stable

<!-- source_link=lib/diagnostics_channel.js -->

The `node:diagnostics_channel` module provides an API to create named channels
to report arbitrary message data for diagnostics purposes.

It can be accessed using:

```mjs
import diagnostics_channel from 'node:diagnostics_channel';
```

```cjs
const diagnostics_channel = require('node:diagnostics_channel');
```

It is intended that a module writer wanting to report diagnostics messages
will create one or many top-level channels to report messages through.
Channels may also be acquired at runtime but it is not encouraged
due to the additional overhead of doing so. Channels may be exported for
convenience, but as long as the name is known it can be acquired anywhere.

If you intend for your module to produce diagnostics data for others to
consume it is recommended that you include documentation of what named
channels are used along with the shape of the message data. Channel names
should generally include the module name to avoid collisions with data from
other modules.
