# kotlin-loader

###Kotlin webpack loader that allows to import Kotlin files into your JS

Hello. This package is not ready for using. If you're interested about it, contact me.

See [examples](https://github.com/huston007/kotlin-loader/tree/master/examples/simple).

Usage:

```sh
npm i webpack-kotlin-loader --save-dev
```


`webpack.config.js`
```js
var path = require('path');
var webpack = require('webpack');

module.exports = {
    context: __dirname,
    devtool: 'source-map',
    entry: {
        main: './entry'
    },
    output: {
        path: __dirname + '/dist',
        filename: 'build.js'
    },
    resolve: {
        alias: {
            //Since compiled kotlin code tries to `require('kotlin')`, we have to tell him where it is
            'kotlin': require.resolve('../../kotlin-runtime')
        }
    },
    module: {
        loaders: [
            {test: /\.kt$/, loaders: ['webpack-kotlin-loader']}
        ]
    }
};
```

Then you could import your kotlin entry point somewhere:
```js
require('./app/app.kt');
```