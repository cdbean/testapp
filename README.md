# Treatment Two: app and module has the same dependency

## Setting
`moduleB@v2` adds dependency on `moduleA`

## Result
The result is the same as the base setting. `moduleA` is installed once as root dependency and bundled once.

`package-lock.json`:

```
"dependencies": {
  "moduleA": {
    "version": "github:imdongchen/moduleA#74041b7e98f82a32de47440fc31b8cffeec85b9c"
  },
  "moduleB": {
    "version": "github:imdongchen/moduleB#5fe53a8059a329a9a1cbbea7f20ffffa9a7a09e3",
    "requires": {
      "moduleA": "github:imdongchen/moduleA#74041b7e98f82a32de47440fc31b8cffeec85b9c"
    }
  }
}
```
