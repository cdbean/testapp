# Treatment Four: multiple modules has conflicting  dependencies

## Setting
Our app adds another dependency, `moduleC`, that depends on `moduleA@v2.`package.json` looks like:

```
  "dependencies": {
    "moduleB": "github:imdongchen/moduleB#v3",
    "moduleA": "github:imdongchen/moduleA",
    "moduleC": "github:imdongchen/moduleC"
  }
```


## Result

`moduleA@v1` will still be installed as the app dependency, and `moduleA@v2` will be installed as both moduleB’s dependency and moduleC’s dependency. And `moduleA@v2` is bundled *twice* in the output.

`package-lock.json`:
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
    },
    "moduleC": {
      "version": "github:imdongchen/moduleC#79700c07ead49bf25cb3fd8240b94e5052bff7a9",
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
