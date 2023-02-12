## Working with JavaScript values

Node-API exposes a set of APIs to create all types of JavaScript values.
Some of these types are documented under [Section 6][]
of the [ECMAScript Language Specification][].

Fundamentally, these APIs are used to do one of the following:

1. Create a new JavaScript object
2. Convert from a primitive C type to a Node-API value
3. Convert from Node-API value to a primitive C type
4. Get global instances including `undefined` and `null`

Node-API values are represented by the type `napi_value`.
Any Node-API call that requires a JavaScript value takes in a `napi_value`.
In some cases, the API does check the type of the `napi_value` up-front.
However, for better performance, it's better for the caller to make sure that
the `napi_value` in question is of the JavaScript type expected by the API.
