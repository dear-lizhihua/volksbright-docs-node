## The Node.js REPL

Node.js itself uses the `node:repl` module to provide its own interactive
interface for executing JavaScript. This can be used by executing the Node.js
binary without passing any arguments (or by passing the `-i` argument):

```console
$ node
> const a = [1, 2, 3];
undefined
> a
[ 1, 2, 3 ]
> a.forEach((v) => {
...   console.log(v);
...   });
1
2
3
```
