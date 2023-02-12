### Troubleshooting: Context loss

In most cases, `AsyncLocalStorage` works without issues. In rare situations, the
current store is lost in one of the asynchronous operations.

If your code is callback-based, it is enough to promisify it with
[`util.promisify()`][] so it starts working with native promises.

If you need to use a callback-based API or your code assumes
a custom thenable implementation, use the [`AsyncResource`][] class
to associate the asynchronous operation with the correct execution context.
Find the function call responsible for the context loss by logging the content
of `asyncLocalStorage.getStore()` after the calls you suspect are responsible
for the loss. When the code logs `undefined`, the last callback called is
probably responsible for the context loss.
