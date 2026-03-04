# code

## WebWorker in webpack
**webpack config:**
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

**use WebWorker:**
```
import MyWorker from '{name}.worker.js'

const worker = new MyWorker()

worker.addEventListener('message', res => console.log(res.data))
worker.postMessage('worker')
```

**Worker file {name}.worker.js:**
```
self.addEventListener('message', function(e) {
    self.postMessage(e.data + '-return')
})
```
