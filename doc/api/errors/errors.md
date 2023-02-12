# Errors

<!--introduced_in=v4.0.0-->

<!--type=misc-->

Applications running in Node.js will generally experience four categories of
errors:

* Standard JavaScript errors such as {EvalError}, {SyntaxError}, {RangeError},
  {ReferenceError}, {TypeError}, and {URIError}.
* System errors triggered by underlying operating system constraints such
  as attempting to open a file that does not exist or attempting to send data
  over a closed socket.
* User-specified errors triggered by application code.
* `AssertionError`s are a special class of error that can be triggered when
  Node.js detects an exceptional logic violation that should never occur. These
  are raised typically by the `node:assert` module.

All JavaScript and system errors raised by Node.js inherit from, or are
instances of, the standard JavaScript {Error} class and are guaranteed
to provide _at least_ the properties available on that class.
