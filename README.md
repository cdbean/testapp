# Treatment One: app and module has no shared dependency

## setting
We have an app that has dependency of `moduleA` and `moduleB`. Neither module themselves has any dependency. 

## Result
Npm installs `moduleA` and `moduleB` as root dependency (under `node_modules`). Check `package-lock.json`.
