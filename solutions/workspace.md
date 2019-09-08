## Intro

In order to share some of the frontend code, the `@dinify/common` package was created, and all of the preveously separate repos were migrated to a a single workspace repository.

## [Packages](https://gitlab.com/dinify/workspace/tree/master/packages)
```
@dinify/common
@dinify/admin
@dinify/app
@dinify/dashboard
@dinify/functions
@dinify/landing
@dinify/waiterboard
```

## Stack
[Lerna](https://github.com/lerna/lerna), [Yarn](https://yarnpkg.com/lang/en/)
[Node version manager](https://github.com/nvm-sh/nvm) (`nvm`)
Node

## Common problems
### Import error: Module not found
Run `yarn install` from the package's directory, or `lerna bootstrap` from the workspace root directory.
#### From `@dinify/common` package
Run this from the workspace root directory to rebuild the common package from source.
```bash
yarn common:build
``` 
Alternatively, navigate to the `common` package from the workspace root directory, with `cd packages/common`, and run `yarn build` to rebuild it.

### `yarn install` or `lerna bootstrap` fails
#### TLDR
```bash
nvm use 10
```
#### Problem
When running either of these commands, this output follows:
```bash
[4/4] 🔨  Building fresh packages...
[1/15] ⠂ node-sass
[-/15] ⠂ waiting...
[-/15] ⠄ waiting...
[4/15] ⠄ fsevents
warning Error running install script for optional dependency: "node_modules/react-scripts/node_modules/fsevents: Command failed.
Exit code: 1
Command: node install
Arguments:
Directory: node_modules/react-scripts/node_modules/fsevents
...
```
It is most likely that this is an incompatibility issue between lerna with yarn workspaces, and node 12. In order to fix it temporarily, downgrade the current environment's node version to 10, by running:
```bash
nvm use 10
```

### Trusted local certificate on OSX
1. Run from workspace root directory
```
open node_modules/webpack-dev-server/ssl
```
2. Open the Keychain Access app
3. Drag and drop `server.pem` in the login keychain
4. Select and open the `localhost` cert that was most recently added
![](/static/keychain-app.png)
5. Expand panel _Trust_ and select _Always Trust_ for _When using this certificate_ dropdown.  
![](/static/update-setting.png)
6. Close the window  
![](/static/close.png)
7. Authenticate user
![](/static/auth-prompt.png)
8. Close everything and refresh development page to see the trusted certificate in the browser

Currently, this needs to be done every time the `webpack-dev-server` generates a new self signed certificate. In other words, every time `lerna bootstrap` or `yarn install` ran, or any script that might be reinstalling the `webpack-dev-server` dependency.

#### Proposed solutions
1. A custom bash script that runs on the [postinstall](https://docs.npmjs.com/misc/scripts#examples) `npm` hook, which installs and marks the certificate as always trusted in the local system's current environment.

2. Prevent `webpack-dev-server` from regenerating the ssl cert, by modifying webpack configuration.