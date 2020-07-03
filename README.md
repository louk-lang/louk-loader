# Louk Loader
Simple loader for using [Louk](https://github.com/louk-lang/louk) with [webpack](https://webpack.js.org).

[![Build Status](https://dev.azure.com/louk-lang/louk-packages/_apis/build/status/Louk%20Loader/Louk%20Loader%20CI?branchName=master)](https://dev.azure.com/louk-lang/louk-packages/_build?definitionScope=%5CLouk%20Loader)
[![Version](https://img.shields.io/npm/v/louk-loader.svg)](https://www.npmjs.com/package/louk-loader)
[![License](https://img.shields.io/github/license/louk-lang/louk-loader.svg)](https://github.com/louk-lang/louk-loader/blob/master/LICENSE)

## Installation
Install `louk-loader` via npm.
```
$ npm install louk-loader -D
```
Also ensure `louk` is installed as a `peerDependency`.
```
$ npm install louk -D
```

## Configuration

### Via Vue Config
If using a [Vue CLI](https://cli.vuejs.org/) project, add a loader via [Vue webpack configuration](https://cli.vuejs.org/guide/webpack.html#simple-configuration).
```js
// vue.config.js
module.exports = {
    /* ... */
    chainWebpack: config => {
    // Louk Loader
    config.module
        .rule('louk')
        .test(/\.louk$/)
        .use("vue-loader")
            .loader("vue-loader")
            .end()
        .use("louk-loader")
            .loader("louk-loader")
    }
}
```

### Via webpack Config
If using a plain webpack project with Vue, add a loader via [webpack configuration](https://webpack.js.org/concepts/loaders/#configuration), in addition to the [Vue Loader](https://vue-loader.vuejs.org/guide/#vue-cli).
```js
// webpack.config.js
module.exports = {
    /* ... */
    module: {
        rules: [
            {
                test: /\.louk$/,
                use: [
                    {loader: "vue-loader"},
                    {loader: "louk-loader"}
                ]
            },
        ]
    }
}
```
