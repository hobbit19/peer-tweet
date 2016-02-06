# PeerTweet

> Decentralized feeds using BitTorrent's DHT. Idea from Arvid and The_8472 "DHT RSS feeds" http://libtorrent.org/dht_rss.html


## Abstract

BitTorrent's DHT is probably one of the most resilient and censorship-resistant networks on the internet. PeerTweet uses this network to allow users to broadcast *tweets* to anyone who is listening. When you start PeerTweet, it generates a hash `@6749b98157c5dd22f6178c38072fe87c08515537` for you which is similar to your Twitter username (ex. `@lmatteis`). The difference is that you have entire control over what can be posted because only you own the private key. Furthermore, thanks to the DHT, what you post cannot be stopped by any government or institution.

Once you find other PeerTweet's accounts you trust (and are not spam), you can follow them. This configures your client to store this user's tweets and broadcasts them to the DHT every once in a while to keep their feed alive. This cooperation of following accounts allows for feeds to stay alive in the DHT network.

# Screenshot

![PeerTweet](http://i.imgur.com/ndCBA8V.png)



## Install

Install dependencies.

```bash
$ npm install
```

## Installing native modules

The app comes with some native bindings. I used this code to make it run on my computer:

Source: https://github.com/atom/electron/blob/master/docs/tutorial/using-native-node-modules.md

```bash
npm install --save-dev electron-rebuild

# Every time you run "npm install", run this
./node_modules/.bin/electron-rebuild

# On Windows if you have trouble, try:
.\node_modules\.bin\electron-rebuild.cmd
```


## Run

Run this two commands __simultaneously__ in different console tabs.

```bash
$ npm run hot-server
$ npm run start-hot
```

*Note: requires a node version >= 4 and an npm version >= 2.*

#### Toggle Chrome DevTools

- OS X: <kbd>Cmd</kbd> <kbd>Alt</kbd> <kbd>I</kbd> or <kbd>F12</kbd>
- Linux: <kbd>Ctrl</kbd> <kbd>Shift</kbd> <kbd>I</kbd> or <kbd>F12</kbd>
- Windows: <kbd>Ctrl</kbd> <kbd>Shift</kbd> <kbd>I</kbd> or <kbd>F12</kbd>

*See [electron-debug](https://github.com/sindresorhus/electron-debug) for more information.*

#### Toggle Redux DevTools

- All platforms: <kbd>Ctrl+H</kbd>

*See [redux-devtools-dock-monitor](https://github.com/gaearon/redux-devtools-dock-monitor) for more information.*


## Externals

If you use any 3rd party libraries which can't be built with webpack, you must list them in your `webpack.config.base.js`：

```javascript
externals: [
  // put your node 3rd party libraries which can't be built with webpack here (mysql, mongodb, and so on..)
]
```

You can find those lines in the file.


## CSS Modules support

Import css file as [css-modules](https://github.com/css-modules/css-modules) using `.module.css`.


## Package

```bash
$ npm run package
```

To package apps for all platforms:

```bash
$ npm run package-all
```

#### Options

- --name, -n: Application name (default: ElectronReact)
- --version, -v: Electron version (default: latest version)
- --asar, -a: [asar](https://github.com/atom/asar) support (default: false)
- --icon, -i: Application icon
- --all: pack for all platforms

Use `electron-packager` to pack your app with `--all` options for darwin (osx), linux and win32 (windows) platform. After build, you will find them in `release` folder. Otherwise, you will only find one for your os.

`test`, `tools`, `release` folder and devDependencies in `package.json` will be ignored by default.

#### Default Ignore modules

We add some module's `peerDependencies` to ignore option as default for application size reduction.

- `babel-core` is required by `babel-loader` and its size is ~19 MB
- `node-libs-browser` is required by `webpack` and its size is ~3MB.

> **Note:** If you want to use any above modules in runtime, for example: `require('babel/register')`, you should move them form `devDependencies` to `dependencies`.

#### Building windows apps from non-windows platforms

Please checkout [Building windows apps from non-windows platforms](https://github.com/maxogden/electron-packager#building-windows-apps-from-non-windows-platforms).


## Native-like UI

If you want to have native-like User Interface (OS X El Capitan and Windows 10), [react-desktop](https://github.com/gabrielbull/react-desktop) may perfect suit for you.


## Maintainers

This is a fork of the https://github.com/chentsulin/electron-react-boilerplate project.

- [C. T. Lin](https://github.com/chentsulin)
- [Jhen-Jie Hong](https://github.com/jhen0409)

## License
MIT