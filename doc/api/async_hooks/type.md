##### `type`

The `type` is a string identifying the type of resource that caused
`init` to be called. Generally, it will correspond to the name of the
resource's constructor.

The `type` of resources created by Node.js itself can change in any Node.js
release. Valid values include `TLSWRAP`,
`TCPWRAP`, `TCPSERVERWRAP`, `GETADDRINFOREQWRAP`, `FSREQCALLBACK`,
`Microtask`, and `Timeout`. Inspect the source code of the Node.js version used
to get the full list.

Furthermore users of [`AsyncResource`][] create async resources independent
of Node.js itself.

There is also the `PROMISE` resource type, which is used to track `Promise`
instances and asynchronous work scheduled by them.

Users are able to define their own `type` when using the public embedder API.

It is possible to have type name collisions. Embedders are encouraged to use
unique prefixes, such as the npm package name, to prevent collisions when
listening to the hooks.
