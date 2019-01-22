### duplexify
---
https://github.com/mafintosh/duplexify

```
npm install duplexify
```

```js
var duplexify = require('duplexify')
var dup = duplexify(writableStream, readableStream)
dup.write('hello')
dup.on('data', function(data){
})

var dup = duplexify()
dup.write('hello')
dup.setReadable(readableStream)
dup.setWritable(writableStream)

dup.on('error', function(err){
  console.log('readable or writable emitted an error - close will follow')
})

dup.on('close', function(){
  console.log('the duplex stream is destroyed')
})
dup.destroy()

var duplexify = require('duplexify');
var http = require('http')
var request = function(opts){
  var req = http.request(opts)
  var dup = duplexify(req)
  req.on('response', function(res){
    dup.setReadable(res)
  })
  return dup
}
var req = request({
  method: 'GET',
  host: 'www.google.com',
  port: 80
})
req.end()
req.pipe(process.stdout)

```
  
```
```


