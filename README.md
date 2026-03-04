# code

## WebWorker in webpack
```
...
config.module
    .rule('worker')
    .test(/\.worker\.js$/)
    .use('worker-loader')
    .loader('worker-loader')
    .options({
        inline: 'fallback', // создаст отдельный файл в dist
        filename: 'js/[name].[contenthash:8].worker.js'
    })
    .end();

// Важно для корректной работы в воркере
config.output.globalObject('this');
...
```
