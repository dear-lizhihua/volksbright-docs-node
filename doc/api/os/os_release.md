## `os.release()`

<!-- YAML
added: v0.3.3
-->

* Returns: {string}

Returns the operating system as a string.

On POSIX systems, the operating system release is determined by calling
[`uname(3)`][]. On Windows, `GetVersionExW()` is used. See
<https://en.wikipedia.org/wiki/Uname#Examples> for more information.
