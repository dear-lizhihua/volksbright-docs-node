## Options for building Node.js

To control how ICU is used in Node.js, four `configure` options are available
during compilation. Additional details on how to compile Node.js are documented
in [BUILDING.md][].

* `--with-intl=none`/`--without-intl`
* `--with-intl=system-icu`
* `--with-intl=small-icu`
* `--with-intl=full-icu` (default)

An overview of available Node.js and JavaScript features for each `configure`
option:

| Feature                                  | `none`                            | `system-icu`                 | `small-icu`            | `full-icu` |
| ---------------------------------------- | --------------------------------- | ---------------------------- | ---------------------- | ---------- |
| [`String.prototype.normalize()`][]       | none (function is no-op)          | full                         | full                   | full       |
| `String.prototype.to*Case()`             | full                              | full                         | full                   | full       |
| [`Intl`][]                               | none (object does not exist)      | partial/full (depends on OS) | partial (English-only) | full       |
| [`String.prototype.localeCompare()`][]   | partial (not locale-aware)        | full                         | full                   | full       |
| `String.prototype.toLocale*Case()`       | partial (not locale-aware)        | full                         | full                   | full       |
| [`Number.prototype.toLocaleString()`][]  | partial (not locale-aware)        | partial/full (depends on OS) | partial (English-only) | full       |
| `Date.prototype.toLocale*String()`       | partial (not locale-aware)        | partial/full (depends on OS) | partial (English-only) | full       |
| [Legacy URL Parser][]                    | partial (no IDN support)          | full                         | full                   | full       |
| [WHATWG URL Parser][]                    | partial (no IDN support)          | full                         | full                   | full       |
| [`require('node:buffer').transcode()`][] | none (function does not exist)    | full                         | full                   | full       |
| [REPL][]                                 | partial (inaccurate line editing) | full                         | full                   | full       |
| [`require('node:util').TextDecoder`][]   | partial (basic encodings support) | partial/full (depends on OS) | partial (Unicode-only) | full       |
| [`RegExp` Unicode Property Escapes][]    | none (invalid `RegExp` error)     | full                         | full                   | full       |

The "(not locale-aware)" designation denotes that the function carries out its
operation just like the non-`Locale` version of the function, if one
exists. For example, under `none` mode, `Date.prototype.toLocaleString()`'s
operation is identical to that of `Date.prototype.toString()`.
