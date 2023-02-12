##### Example

```json
{
  "scopes": {
    "file:///C:/app/": {},
    "file:": {},
    "": {}
  }
}
```

Given a file located at `file:///C:/app/bin/main.js`, the following scopes would
be checked in order:

1. `"file:///C:/app/bin/"`

This determines the policy for all file based resources within
`"file:///C:/app/bin/"`. This is not in the `"scopes"` field of the policy and
would be skipped. Adding this scope to the policy would cause it to be used
prior to the `"file:///C:/app/"` scope.

2. `"file:///C:/app/"`

This determines the policy for all file based resources within
`"file:///C:/app/"`. This is in the `"scopes"` field of the policy and it would
determine the policy for the resource at `file:///C:/app/bin/main.js`. If the
scope has `"cascade": true`, any unsatisfied queries about the resource would
delegate to the next relevant scope for `file:///C:/app/bin/main.js`, `"file:"`.

3. `"file:///C:/"`

This determines the policy for all file based resources within `"file:///C:/"`.
This is not in the `"scopes"` field of the policy and would be skipped. It would
not be used for `file:///C:/app/bin/main.js` unless `"file:///"` is set to
cascade or is not in the `"scopes"` of the policy.

4. `"file:///"`

This determines the policy for all file based resources on the `localhost`. This
is not in the `"scopes"` field of the policy and would be skipped. It would not
be used for `file:///C:/app/bin/main.js` unless `"file:///"` is set to cascade
or is not in the `"scopes"` of the policy.

5. `"file:"`

This determines the policy for all file based resources. It would not be used
for `file:///C:/app/bin/main.js` unless `"file:///"` is set to cascade or is not
in the `"scopes"` of the policy.

6. `""`

This determines the policy for all resources. It would not be used for
`file:///C:/app/bin/main.js` unless `"file:"` is set to cascade.
