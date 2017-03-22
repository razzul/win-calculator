# win-calculator

[download [x32]](https://drive.google.com/open?id=0B5vssmhQnZ0Ed0JlcGloa0JFTzg)

A basic Electron application needs just these files:

- `package.json` - Points to the app's main file and lists its details and dependencies.
- `main.js` - Starts the app and creates a browser window to render HTML. This is the app's **main process**.
- `index.html` - A web page to render. This is the app's **renderer process**.

## To Use

To clone and run this repository you'll need [Git](https://git-scm.com) and [Node.js](https://nodejs.org/en/download/) (which comes with [npm](http://npmjs.com)) installed on your computer. From your command line:

```bash
# Clone this repository
git clone https://github.com/razzul/win-calculator
# Go into the repository
cd win-calculator
# Install dependencies
npm install
# Run the app
npm start
```

```bash
npm i electron-builder
```

> **Note:** _Platform specific 7zip-bin-* packages are optionalDependencies, which may require manual install if you have npm configured to not install optional deps by default._

## Quick Setup Guide

1. Specify the standard fields in the application `package.json` — [name](https://github.com/electron-userland/electron-builder/wiki/Options#AppMetadata-name), `description`, `version` and [author](https://docs.npmjs.com/files/package.json#people-fields-author-contributors).

2. Specify the [build](https://github.com/electron-userland/electron-builder/wiki/Options#build) configuration in the `package.json` as follows:
    ```json
    "build": {
      "appId": "your.id",
      "mac": {
        "category": "your.app.category.type"
      }
    }
    ```
   See [all options](https://github.com/electron-userland/electron-builder/wiki/Options).

3. Create a directory [build](https://github.com/electron-userland/electron-builder/wiki/Options#MetadataDirectories-buildResources) in the root of the project and save a `background.png` (macOS DMG background), `icon.icns` (macOS app icon) and `icon.ico` (Windows app icon) into it.

   <a id="user-content-linuxIcon" class="anchor" href="#linuxIcon" aria-hidden="true"></a>The Linux icon set will be generated automatically based on the macOS `icns` file (or you can put them into the `build/icons` directory if you want to specify them yourself. The filename must contain the size (e.g. `32x32.png`) of the icon).

4. Add the [scripts](https://docs.npmjs.com/cli/run-script) key to the development `package.json`:
    ```json
    "scripts": {
      "pack": "build --dir",
      "dist": "build"
    }
    ```
    Then you can run `npm run dist` (to package in a distributable format (e.g. dmg, windows installer, deb package)) or `npm run pack` (only generates the package directory without really packaging it. This is useful for testing purposes).

    To ensure your native dependencies are always matched electron version, simply add `"postinstall": "install-app-deps"` to your `package.json`.

5. If you have native addons of your own that are part of the application (not as a dependency), add `"nodeGypRebuild": true` to the `build` section of your development `package.json`.  
   :bulb: Don't [use](https://github.com/electron-userland/electron-builder/issues/683#issuecomment-241214075) [npm](http://electron.atom.io/docs/tutorial/using-native-node-modules/#using-npm) (neither `.npmrc`) for configuring electron headers. Use [node-gyp-rebuild](https://github.com/electron-userland/electron-builder/issues/683#issuecomment-241488783) bin instead.

   
6. Installing the [required system packages](https://github.com/electron-userland/electron-builder/wiki/Multi-Platform-Build).

Please note that everything is packaged into an asar archive [by default](https://github.com/electron-userland/electron-builder/wiki/Options#Config-asar).

For an app that will be shipped to production, you should sign your application. See [Where to buy code signing certificates](https://github.com/electron-userland/electron-builder/wiki/Code-Signing#where-to-buy-code-signing-certificate).

## Auto Update
`electron-builder` produces all required artifacts, for example, for macOS:

* `.dmg`: macOS installer, required for the initial installation process on macOS.
* `-mac.zip`: required for Squirrel.Mac.

See the [Auto Update](https://github.com/electron-userland/electron-builder/wiki/Auto-Update) section of the [Wiki](https://github.com/electron-userland/electron-builder/wiki).

![alt tag](https://raw.githubusercontent.com/razzul/win-calculator/master/screenshots/1.png)
![alt tag](https://raw.githubusercontent.com/razzul/win-calculator/master/screenshots/2.png)
