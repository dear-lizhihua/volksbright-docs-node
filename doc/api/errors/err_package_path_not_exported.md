### `ERR_PACKAGE_PATH_NOT_EXPORTED`

The `package.json` [`"exports"`][] field does not export the requested subpath.
Because exports are encapsulated, private internal modules that are not exported
cannot be imported through the package resolution, unless using an absolute URL.

<a id="ERR_PARSE_ARGS_INVALID_OPTION_VALUE"></a>
