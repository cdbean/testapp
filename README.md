# Treatment One: app and module has no shared dependency

## Setting
We have an app that has dependency of `moduleA` and `moduleB`. Neither module themselves has any dependency. `package.json` looks like:

```
"dependencies": {
  "moduleA": "github:imdongchen/moduleA",
  "moduleB": "github:imdongchen/moduleB"
}
```

## Result
Npm installs `moduleA` and `moduleB` as root dependency (under `node_modules`). `package-lock.json` looks like:

```
"dependencies": {
  "moduleA": {
    "version": "github:imdongchen/moduleA#74041b7e98f82a32de47440fc31b8cffeec85b9c"
  },
  "moduleB": {
    "version": "github:imdongchen/moduleB#9f5fa8d59032077aa0458fd4aaa753be12b9dd26"
  }
```
