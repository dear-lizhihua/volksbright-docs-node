### `message.trailersDistinct`

<!-- YAML
added:
  - v18.3.0
  - v16.17.0
-->

* {Object}

Similar to [`message.trailers`][], but there is no join logic and the values are
always arrays of strings, even for headers received just once.
Only populated at the `'end'` event.
