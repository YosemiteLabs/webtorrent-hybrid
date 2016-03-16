# WebTorrent (with WebRTC support in Node.js)

[![Build Status][webtorrent-ti]][webtorrent-tu]
[![NPM Version][webtorrent-ni]][webtorrent-nu]
[![NPM Downloads][webtorrent-downloads-image]][webtorrent-downloads-url]

### Streaming torrent client for node environments

In node.js, the `webtorrent` package only connects to normal TCP/UDP peers, not WebRTC peers. If you want to connect to all types of peers, including WebRTC peers, from node.js, you need to use this package (`webtorrent-hybrid`).

Previous versions (0.x) of this package used [wrtc](https://github.com/js-platform/node-webrtc), a WebRTC implementation via native extensions, the current one is based on [electron-webrtc](https://github.com/mappum/electron-webrtc) (which in turn uses [electron-prebuilt](https://github.com/electron-userland/electron-prebuilt)) for better compatibility. It creates a hidden Electron process (which is based on Chromium, so WebRTC support is great!) and communicates with that process to enable WebRTC in Node.js. This adds a lot of overhead, so we are looking forward to using a pure JavaScript implementation, like perhaps [Node-RTCPeerConnection](https://github.com/nickdesaulniers/node-rtc-peer-connection) when it's ready.

To run this package on a headless server execute [the provided script](bin/prepareHeadless.sh) or follow [these instructions](https://github.com/mappum/electron-webrtc#running-on-a-headless-server).

[![js-standard-style](https://cdn.rawgit.com/feross/standard/master/badge.svg)](https://github.com/feross/standard)

## Install

The current version of `webtorrent-hybrid` requires an screen as the headless electron expects one. In case that you are running in a screenless environment you must use a virtual screen such as `xvfb`. You must first install it and run it. For Debian based OSs:

```bash
sudo apt-get install xvfb
export DISPLAY='0:99'
Xvfb :99 -screen 0 1024x768x24 > /dev/null 2>&1 &
```

For Centos/rhel:
```bash
sudo yum install xorg-x11-server-Xvfb
export DISPLAY='0:99'
Xvfb :99 -screen 0 1024x768x24 > /dev/null 2>&1 &
```

Also, if you're running webtorrent-hybrid in a node.js project, you can start Xvfb within your app:
```bash
npm install xvfb

var Xvfb = require('xvfb')
var xvfb = new Xvfb()
xvfb.startSync()

Webtorrent = require('webtorrent-hybrid')
```

To install WebTorrent:

```bash
npm install webtorrent-hybrid
```

To install a `webtorrent-hybrid` command line program, run:

```bash
npm install webtorrent-hybrid -g
```

## Usage

`webtorrent-hybrid` has the same command line interface (CLI) and module API as
[`webtorrent`](https://github.com/feross/webtorrent). Just `require('webtorrent-hybrid')`
instead of `require('webtorrent')`.

See the [WebTorrent docs](https://github.com/feross/webtorrent).

## License

MIT. Copyright (c) [Feross Aboukhadijeh](http://feross.org).

[webtorrent]: https://github.com/feross/webtorrent-hybrid
[webtorrent-ti]: https://img.shields.io/travis/feross/webtorrent-hybrid/master.svg
[webtorrent-tu]: https://travis-ci.org/feross/webtorrent-hybrid
[webtorrent-ni]: https://img.shields.io/npm/v/webtorrent-hybrid.svg
[webtorrent-nu]: https://npmjs.org/package/webtorrent-hybrid
[webtorrent-downloads-image]: https://img.shields.io/npm/dm/webtorrent-hybrid.svg
[webtorrent-downloads-url]: https://npmjs.org/package/webtorrent-hybrid
[webtorrent-gratipay-image]: https://img.shields.io/gratipay/feross.svg
[webtorrent-gratipay-url]: https://gratipay.com/feross/
[webtorrent-sauce-image]: https://saucelabs.com/browser-matrix/webtorrent-hybrid.svg
[webtorrent-sauce-url]: https://saucelabs.com/u/webtorrent-hybrid
