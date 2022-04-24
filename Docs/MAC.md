# Mac Electron App build, Github Release with Actions

## Build and Release

Clone the repo

```sh
git clone https://github.com/TelicSolutionsInc/AngularBoilerplate.git
```

Run npm install

```sh
npm install
```

Firstly build the project before building the package.

```sh
npm run build
```

Run npm run package-mac to build .exe file of your Electron App

```sh
npm run package-mac
```

A "release-builds" folder will be created in the root directory of your project having mac/darwin folder with .exe file of your electron app.
You can directly execute the .exe file to open the application in Mac.

### Actions

This is a Github Action that can be used to build and then release the Mac package as an artifact on Github Actions tab.
![](images/../../images/mac.png)

Actions for Mac:

```sh
name: Linux Build on PR
on:
  push:
    branches: [ master ]
jobs:
  Mac-Release:
    runs-on: macos-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v2
      - name: cache node module
        id: myCacheStep
        uses: actions/cache@v2
        env:
          cache-name: cache-node-modules
        with:
          path: node_modules
          key: ${{ runner.os }}-build-${{ env.cache-name }}-${{ hashFiles('**/package-lock.json') }}
          restore-keys: |
            ${{ runner.os }}-build-${{ env.cache-name }}-
            ${{ runner.os }}-build-
            ${{ runner.os }}-
      - name: Install Dependencies
        if: steps.myCacheStep.outputs.cache-hit != 'true'
        run: npm install
      - name: Build Using npm
        run: npm run build
      - name: mac package
        run: npm run package-mac
      - name: Use the Upload Artifact GitHub Action
        uses: actions/upload-artifact@v2
        with:
          name: Mac Release Fodler
          path: release-builds
```

This will produce a zipped folder for the respective action.
