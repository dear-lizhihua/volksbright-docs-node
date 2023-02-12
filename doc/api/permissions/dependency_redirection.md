##### Dependency redirection

An application may need to ship patched versions of modules or to prevent
modules from allowing all modules access to all other modules. Redirection
can be used by intercepting attempts to load the modules wishing to be
replaced.

```json
{
  "resources": {
    "./app/checked.js": {
      "dependencies": {
        "fs": true,
        "os": "./app/node_modules/alt-os",
        "http": { "import": true }
      }
    }
  }
}
```

The dependencies are keyed by the requested specifier string and have values
of either `true`, `null`, a string pointing to a module to be resolved,
or a conditions object.

The specifier string does not perform any searching and must match exactly what
is provided to the `require()` or `import` except for a canonicalization step.
Therefore, multiple specifiers may be needed in the policy if it uses multiple
different strings to point to the same module (such as excluding the extension).

Specifier strings are canonicalized but not resolved prior to be used for
matching in order to have some compatibility with import maps, for example if a
resource `file:///C:/app/server.js` was given the following redirection from a
policy located at `file:///C:/app/policy.json`:

```json
{
  "resources": {
    "file:///C:/app/utils.js": {
      "dependencies": {
        "./utils.js": "./utils-v2.js"
      }
    }
  }
}
```

Any specifier used to load `file:///C:/app/utils.js` would then be intercepted
and redirected to `file:///C:/app/utils-v2.js` instead regardless of using an
absolute or relative specifier. However, if a specifier that is not an absolute
or relative URL string is used, it would not be intercepted. So, if an import
such as `import('#utils')` was used, it would not be intercepted.

If the value of the redirection is `true`, a "dependencies" field at the top of
the policy file will be used. If that field at the top of the policy file is
`true` the default node searching algorithms are used to find the module.

If the value of the redirection is a string, it is resolved relative to
the manifest and then immediately used without searching.

Any specifier string for which resolution is attempted and that is not listed in
the dependencies results in an error according to the policy.

Redirection does not prevent access to APIs through means such as direct access
to `require.cache` or through `module.constructor` which allow access to
loading modules. Policy redirection only affects specifiers to `require()` and
`import`. Other means, such as to prevent undesired access to APIs through
variables, are necessary to lock down that path of loading modules.

A boolean value of `true` for the dependencies map can be specified to allow a
module to load any specifier without redirection. This can be useful for local
development and may have some valid usage in production, but should be used
only with care after auditing a module to ensure its behavior is valid.

Similar to `"exports"` in `package.json`, dependencies can also be specified to
be objects containing conditions which branch how dependencies are loaded. In
the preceding example, `"http"` is allowed when the `"import"` condition is
part of loading it.

A value of `null` for the resolved value causes the resolution to fail. This
can be used to ensure some kinds of dynamic access are explicitly prevented.

Unknown values for the resolved module location cause failures but are
not guaranteed to be forward compatible.
