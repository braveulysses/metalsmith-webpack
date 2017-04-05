# metalsmith-webpack2

[![Build Status](https://travis-ci.org/braveulysses/metalsmith-webpack2.svg?branch=master)](https://travis-ci.org/braveulysses/metalsmith-webpack2)

A [Webpack 2][webpack] plugin for [Metalsmith][metalsmith].

## Installation

```
npm install metalsmith-webpack2
```

## Usage

```js
var webpack = require('metalsmith-webpack2')

Metalsmith(__dirname)
  .use(webpack(options))
  .build()
```

### Options

See the [Webpack configuration][webpack configuration] documentation for details.

## Example

It's best to store the files to be processed by Webpack (css, js, and so on) in a separate directory in your `src` directory (e.g. `src/webpack`) so that you can easily generate all of them at once. We also recommend that you output them to the `src` directory (e.g., `src/assets/gen`) so that they will end up in the right place in the Metalsmith build destination, although they will not appear on the filesystem itself, as the results are only stored in memory.

```js
Metalsmith(__dirname)
  .use(webpack({
    entry: {
      index: './src/webpack/js/index.js'
    },
    output: {
      path: __dirname + '/src/static/gen',
      filename: '[name].js'
    }
  }))
  .build()
```

If you do not want the source files to be included in the Metalsmith build destination, you can instruct Metalsmith to ignore the path for those source files. For example, to ignore the path `src/webpack` from the example above, you could use `.ignore('webpack')`; then the compiled files in `src/staic/gen` would show up in the build, but not the source files.

See the [tests][tests] for more examples.

## Tests

```
$ npm test
```

## License

MIT License, see [LICENSE](https://github.com/braveulysses/metalsmith-webpack2/blob/master/LICENSE.md) for details.

[metalsmith]: http://www.metalsmith.io/
[tests]: https://github.com/braveulysses/metalsmith-webpack2/blob/master/test/index.js
[webpack]: https://webpack.js.org/
[webpack configuration]: https://webpack.js.org/configuration/
