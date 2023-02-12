# scream.coffee
export scream = (str) -> str.toUpperCase()
```

With the preceding loader, running
`node --experimental-loader ./coffeescript-loader.mjs main.coffee`
causes `main.coffee` to be turned into JavaScript after its source code is
loaded from disk but before Node.js executes it; and so on for any `.coffee`,
`.litcoffee` or `.coffee.md` files referenced via `import` statements of any
loaded file.
