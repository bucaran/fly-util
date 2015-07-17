> Utilities for Fly Plugins

[![][fly-badge]][fly]
[![npm package][npm-ver-link]][fly-util]
[![][dl-badge]][npm-pkg-link]
[![][travis-logo]][travis]
![][mit-badge]


<p align="center">
  <a href="http://github.com/flyjs/fly-util">
    <img width=180px  src="https://cloud.githubusercontent.com/assets/8317250/8733685/0be81080-2c40-11e5-98d2-c634f076ccd7.png">
  </a>
</p>


<p align="center">
  <b><a href="#about">About</a></b>
  |
  <b><a href="#install">Install</a></b>
  |
  <b><a href="#usage">Usage</a></b>
  |
  <b><a href="#api">API</a></b>
</p>


## About

[_Fly_][fly] is a modern [build system](https://en.wikipedia.org/wiki/Build_automation) for [Node](https://nodejs.org/) based in [_co_-routines](https://medium.com/@tjholowaychuk/callbacks-vs-coroutines-174f1fe66127), [generators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/function*) and [promises](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise).

This repository contains the `fly-util` package with utilities you can use in your own _Fly_ [plugins](/docs/README.md#plugins).


## Install

```
npm install fly-util
```

## Usage

> Not all _Fly_ plugins use these utilities. For plugins that do, see [this list](https://github.com/flyjs/fly-util/wiki/Plugins-Using-Utilities).


```js
import util from "fly-util"
```

```js
const util = require("fly-util")
```

## API

## `log`
```js
function log (...args)
```
Wrapper for `Console.log`.

## `error`
```js
function error (...args)
```
Wrapper for `Console.error`.

## `warn`
```js
function warn (...args)
```
Wrapper for `Console.log` in a distinctive color. Output is suppressed if `process.env.SILENT` is truthy.

## `debug`
```js
function debug (...args)
```
Wrapper for `Console.log` in a distinctive color. Output is displayed only if `process.env.DEBUG` is truthy.

## `trace`
 ```js
function trace (e)
```
+ `e {Object}` error object

Wrapper for [`prettyjson`](https://github.com/rafeca/prettyjson).

## `defer`
```js
function defer (asyncFunc)
```
+ `asyncFunc {Function}` async function of the form (value, options, cb)
+ `return` `{Function}` new function that returns a promise

Promisify a function with a callback.

## `flatten`
```js
function flatten (array)
```
+ `array {Array}`
+ `return` `[[a],[b],[c]] → [a,b,c]`

Flatten a nested array recursively.

## `searchPlugins`
```js
function findPlugins (pkg, blacklist = [])
```
+ `pkg {Package}` project's package.json
+ `blacklist {Array}` blacklisted plugins
+ `return {Array}` list of fly dependencies that can be loaded

Find `fly-*` plugins listed in package.json dependencies.

## `expand`
```js
function expand (pattern, options)
```
+ `pattern {String}` Pattern to match
+ `handler {Object}` [options](https://github.com/isaacs/node-glob#options) to glob
+ `return {Promise}`

Promisified [glob](https://github.com/isaacs/node-glob) wrapper.

## `watch`
```js
function watch (globs, options)
```
+ `globs {Array:String}` globs to watch
+ `options {Object}` chokidar [options](https://github.com/paulmillr/chokidar#api)
+ `return {chokidar.FSWatcher}`

Wrapper for [chokidar.watch](https://github.com/paulmillr/chokidar).

## `notifyUpdates`
```js
function notifyUpdates (options)
```
+ `options {Array}` options

Wrapper for [update-notifier](https://github.com/yeoman/update-notifier).

## `findFlypath`
```js
function* findPath (path, names)
```
+ `path {String}` file or path to the Flyfile
+ `names {[String]}` Optional. list of alternative Flyfile names
+ `return {String}` path to the Flyfile

Find a Flyfile in the given path. If `path` is a directory find the first Flyfile by extension. Flyfiles can be written in any language supported in [interpret/jsVariants](https://github.com/tkellen/js-interpret).


## Dependencies

+ [`mz/fs`](https://github.com/normalize/mz) promise wrapped basic IO handling

+ [`clor`](https://github.com/bucaran/clor) terminal colors

+ [`glob`](https://github.com/isaacs/node-glob) expanding path/file glob patterns

+ [`prettyjson`](https://github.com/rafeca/prettyjson) pretty formatting for JSON objects

+ [`chokidar`](https://gitter.im/paulmillr/chokidar) watch IO events.

+ [`interpret`](https://github.com/tkellen/js-interpret) resolve modules for in-the-fly transpilation of ES6, CoffeeScript, Earl Grey, etc.

+ [`update-notifier`](https://github.com/yeoman/update-notifier) CLI update notifications

# License

[MIT](http://opensource.org/licenses/MIT) © [Jorge Bucaran][Author] et [al][contributors]
:heart:

[author]: http://about.bucaran.me
[contributors]: https://github.com/flyjs/fly-util/graphs/contributors
[fly]: https://www.github.com/flyjs/fly
[fly-util]: https://www.github.com/flyjs/fly-util
[fly-badge]: https://img.shields.io/badge/fly-JS-05B3E1.svg?style=flat-square
[mit-badge]: https://img.shields.io/badge/license-MIT-444444.svg?style=flat-square
[npm-pkg-link]: https://www.npmjs.org/package/fly-util
[npm-ver-link]: https://img.shields.io/npm/v/fly-util.svg?style=flat-square
[dl-badge]: http://img.shields.io/npm/dm/fly-util.svg?style=flat-square
[travis-logo]: http://img.shields.io/travis/flyjs/fly-util.svg?style=flat-square
[travis]: https://travis-ci.org/flyjs/fly-util
