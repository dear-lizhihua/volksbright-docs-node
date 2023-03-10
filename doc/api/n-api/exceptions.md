### Exceptions

Any Node-API function call may result in a pending JavaScript exception. This is
the case for any of the API functions, even those that may not cause the
execution of JavaScript.

If the `napi_status` returned by a function is `napi_ok` then no
exception is pending and no additional action is required. If the
`napi_status` returned is anything other than `napi_ok` or
`napi_pending_exception`, in order to try to recover and continue
instead of simply returning immediately, [`napi_is_exception_pending`][]
must be called in order to determine if an exception is pending or not.

In many cases when a Node-API function is called and an exception is
already pending, the function will return immediately with a
`napi_status` of `napi_pending_exception`. However, this is not the case
for all functions. Node-API allows a subset of the functions to be
called to allow for some minimal cleanup before returning to JavaScript.
In that case, `napi_status` will reflect the status for the function. It
will not reflect previous pending exceptions. To avoid confusion, check
the error status after every function call.

When an exception is pending one of two approaches can be employed.

The first approach is to do any appropriate cleanup and then return so that
execution will return to JavaScript. As part of the transition back to
JavaScript, the exception will be thrown at the point in the JavaScript
code where the native method was invoked. The behavior of most Node-API calls
is unspecified while an exception is pending, and many will simply return
`napi_pending_exception`, so do as little as possible and then return to
JavaScript where the exception can be handled.

The second approach is to try to handle the exception. There will be cases
where the native code can catch the exception, take the appropriate action,
and then continue. This is only recommended in specific cases
where it is known that the exception can be safely handled. In these
cases [`napi_get_and_clear_last_exception`][] can be used to get and
clear the exception. On success, result will contain the handle to
the last JavaScript `Object` thrown. If it is determined, after
retrieving the exception, the exception cannot be handled after all
it can be re-thrown it with [`napi_throw`][] where error is the
JavaScript value to be thrown.

The following utility functions are also available in case native code
needs to throw an exception or determine if a `napi_value` is an instance
of a JavaScript `Error` object: [`napi_throw_error`][],
[`napi_throw_type_error`][], [`napi_throw_range_error`][], [`node_api_throw_syntax_error`][] and [`napi_is_error`][].

The following utility functions are also available in case native
code needs to create an `Error` object: [`napi_create_error`][],
[`napi_create_type_error`][], [`napi_create_range_error`][] and [`node_api_create_syntax_error`][],
where result is the `napi_value` that refers to the newly created
JavaScript `Error` object.

The Node.js project is adding error codes to all of the errors
generated internally. The goal is for applications to use these
error codes for all error checking. The associated error messages
will remain, but will only be meant to be used for logging and
display with the expectation that the message can change without
SemVer applying. In order to support this model with Node-API, both
in internal functionality and for module specific functionality
(as its good practice), the `throw_` and `create_` functions
take an optional code parameter which is the string for the code
to be added to the error object. If the optional parameter is `NULL`
then no code will be associated with the error. If a code is provided,
the name associated with the error is also updated to be:

```text
originalName [code]
```

where `originalName` is the original name associated with the error
and `code` is the code that was provided. For example, if the code
is `'ERR_ERROR_1'` and a `TypeError` is being created the name will be:

```text
TypeError [ERR_ERROR_1]
```
