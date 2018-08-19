# Louk Loader
Simple loader for using [Louk](https://github.com/agorischek/louk) with [webpack](https://webpack.js.org).

## Installation
```
$ npm install louk-loader -D
```

## Content

### In Single-File Components
Vue [Single-File Components](https://vuejs.org/v2/guide/single-file-components.html) can use Louk in their `template` by including the `lang=louk` attribute.
```
///App.vue
<template lang="louk">
    div
        h1 name
</template>

<script>
    module.exports = {
      data: function () {
        return {
            name: "Louk",
        }
      }
    }
</script>
```

### In Standalone Files
Louk content can also be imported from standalone `.louk` files.
```
//index.js
const doc = require("./example-docs/doc.louk")
```
```
//doc.louk
div
    h1 name
```

## Configuration
Ensure `louk` is installed as a `peerDependency`, then configure your build pipeline:

### Via Vue Config
If using a [Vue CLI](https://cli.vuejs.org/) project, add a loader via [Vue webpack configuration](https://cli.vuejs.org/guide/webpack.html#simple-configuration).
```
// vue.config.js
module.exports = {
    /* ... */
    chainWebpack: config => {
        // Louk Loader
        config.module
            .rule("louk")
            .test(/\.louk$/)
            .use()
                .loader("louk""))
                .end()
  }
}
```

### Via webpack Config with Vue
If using a plain webpack project with Vue, add a loader via [webpack configuration](https://webpack.js.org/concepts/loaders/#configuration), in addition to the [Vue Loader](https://vue-loader.vuejs.org/guide/#vue-cli).
```
// webpack.config.js
module.exports = {
    /* ... */
    module: {
        rules: [
            {
                test: /\.louk$/,
                loader: "louk-loader"
            }
        ]
    }
}
```

### Via webpack Config without Vue
If using a plain webpack project without Vue, add both the `louk-loader` and an `html-loader`.
```
// webpack.config.js
module.exports = {
    /* ... */
    module: {
        rules: [
            {
                test: /\.louk$/,
                use: [
                    {
                        loader: "html-loader"
                    },
                    {
                        loader: "louk-loader"),
                    }
                ]
            },
        ]
    }
}
```
