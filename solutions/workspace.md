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

### New proposed packages

Reusable, mostly dumb and stateless view layer components.

```
@dinify/components
```

Documentation for the Dinify platform.

```
@dinify/docs
```

Common utility functions, libraries, and code that is not specific to any of the products. Migrate and split `@dinify/common` into `core` and `components`. No dependency on react or any browser context specific stuff.

```
@dinify/core
```

Typescript tpye definitions, module definitions, interfaces, and so on.

```
@dinify/types
```

## Current solution

### Stack

[Lerna](https://github.com/lerna/lerna)  
[Yarn](https://yarnpkg.com/lang/en/) (using yarn workspaces)  
[Node version manager](https://github.com/nvm-sh/nvm) (`nvm`)  
Node

### Description

All clientside code has been moved to a single folder, in a single [workspace repository](https://gitlab.com/dinify/workspace). Prefixing with the package name (like `App: commit message`) in git commits have been introduced to try to organize changes.

## Other proposed solutions

1. Using `git+ssh` or `git+https` prefix in `package.json` dependencies

```json
"@dinify/app": "git+ssh://git@gitlab.com:dinify/packages/app.git"
```

2. Using bultin npm GitLab integration

```bash
npm install gitlab:gitlabname/gitlabrepo[#commit-ish]
```

3. Using `npm` to publish packages to a registry, such as npm private registry or GitHub package registry.

## Imports

### Design goals

Any ES6 or typescript module should be able to import from the `@dinify` workspace, without having to rebuild any of the packages. All imports within a single package should be able to be configured using the `baseUrl` attribute in
`tsconfig.json` in the package directory. The `tsconfig.json` the in workspace root should point all packages to the `src` directory by default.

## Common problems

### Webpack issues, general WTF

The error message depends on the package. These types of errors pop up after moving dependencies from one package to the other, or adding / removing dependencies on individual packages.

Most recent example:

```
TypeError: Cannot assign to read only property 'exports' of object '#<Object>'
```

Solution is to make sure there are no version conflicts between packages, so the version for the dependency in question (inferred from the stack trace of the error) matches in all `package.json` files.

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

**Simple and fast:** open the page in Safari, then expand the warning panel about the certificate, and click "visit this website". Since Safari is better integrated with the OS, there is an auth prompt as soon as you visit the site and it automatically adds the certificate to your keychain.

**Manual**

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
