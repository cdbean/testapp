# Treatment Three: app and module has conflicting dependency

## Setting
 `moduleA` has a new version `v2`, and `moduleB` upgrades to `v3`, which depends on `moduleA@v2`. Yet app still has dependency on `moduleA@v1`. Our `package.json` looks like
 
 ```
 "dependencies": {
  "moduleA": "github:imdongchen/moduleA",
  "moduleB": "github:imdongchen/moduleB#v3"
}
 ```
 
 ## Result
 `moduleA@v1` is installed in `node_modules/` and `moduleA@v2` is installed in `node_modules/moduleB/node_modules/`. The output bundle includes both versions of moduleA. The `package-lock.json` looks like:

```
"dependencies": {
  "moduleA": {
    "version": "github:imdongchen/moduleA#74041b7e98f82a32de47440fc31b8cffeec85b9c"
  },
  "moduleB": {
    "version": "github:imdongchen/moduleB#78d90dfe3a17b3370abb5c5039cc660a1eecc024",
    "requires": {
      "moduleA": "github:imdongchen/moduleA#2d86476f550d7ccfb0f089dc6c13cc13d8a9427b"
    },
    "dependencies": {
      "moduleA": {
        "version": "github:imdongchen/moduleA#2d86476f550d7ccfb0f089dc6c13cc13d8a9427b"
      }
    }
  }
```
