#### `eventTarget.dispatchEvent(event)`

<!-- YAML
added: v14.5.0
-->

* `event` {Event}
* Returns: {boolean} `true` if either event's `cancelable` attribute value is
  false or its `preventDefault()` method was not invoked, otherwise `false`.

Dispatches the `event` to the list of handlers for `event.type`.

The registered event listeners is synchronously invoked in the order they
were registered.
