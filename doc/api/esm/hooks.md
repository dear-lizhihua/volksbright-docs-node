### Hooks

Hooks are part of a chain, even if that chain consists of only one custom
(user-provided) hook and the default hook, which is always present. Hook
functions nest: each one must always return a plain object, and chaining happens
as a result of each function calling `next<hookName>()`, which is a reference
to the subsequent loader's hook.

A hook that returns a value lacking a required property triggers an exception.
A hook that returns without calling `next<hookName>()` _and_ without returning
`shortCircuit: true` also triggers an exception. These errors are to help
prevent unintentional breaks in the chain.
