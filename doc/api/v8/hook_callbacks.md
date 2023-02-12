### Hook callbacks

Key events in the lifetime of a promise have been categorized into four areas:
creation of a promise, before/after a continuation handler is called or around
an await, and when the promise resolves or rejects.

While these hooks are similar to those of [`async_hooks`][] they lack a
`destroy` hook. Other types of async resources typically represent sockets or
file descriptors which have a distinct "closed" state to express the `destroy`
lifecycle event while promises remain usable for as long as code can still
reach them. Garbage collection tracking is used to make promises fit into the
`async_hooks` event model, however this tracking is very expensive and they may
not necessarily ever even be garbage collected.

Because promises are asynchronous resources whose lifecycle is tracked
via the promise hooks mechanism, the `init()`, `before()`, `after()`, and
`settled()` callbacks _must not_ be async functions as they create more
promises which would produce an infinite loop.

While this API is used to feed promise events into [`async_hooks`][], the
ordering between the two is undefined. Both APIs are multi-tenant
and therefore could produce events in any order relative to each other.
