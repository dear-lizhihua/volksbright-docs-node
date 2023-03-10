# Domain

<!-- YAML
deprecated: v1.4.2
changes:
  - version: v8.8.0
    pr-url: https://github.com/nodejs/node/pull/15695
    description: Any `Promise`s created in VM contexts no longer have a
                 `.domain` property. Their handlers are still executed in the
                 proper domain, however, and `Promise`s created in the main
                 context still possess a `.domain` property.
  - version: v8.0.0
    pr-url: https://github.com/nodejs/node/pull/12489
    description: Handlers for `Promise`s are now invoked in the domain in which
                 the first promise of a chain was created.
-->

<!--introduced_in=v0.10.0-->

> Stability: 0 - Deprecated

<!-- source_link=lib/domain.js -->

**This module is pending deprecation.** Once a replacement API has been
finalized, this module will be fully deprecated. Most developers should
**not** have cause to use this module. Users who absolutely must have
the functionality that domains provide may rely on it for the time being
but should expect to have to migrate to a different solution
in the future.

Domains provide a way to handle multiple different IO operations as a
single group. If any of the event emitters or callbacks registered to a
domain emit an `'error'` event, or throw an error, then the domain object
will be notified, rather than losing the context of the error in the
`process.on('uncaughtException')` handler, or causing the program to
exit immediately with an error code.
