##### 第一章

###### 1.特性

- node.js可以解析js代码，没有浏览器安全级别的限制（node不会跨域），提供了很多系统级别的API，如：文件的读写，进程的管理以及网络通信等

- node有三个模块：内置模块、自定义模块和第三方模块

###### 2.http

```javascript
// 开启一个服务 
// 可以在本地跑起来
const http = require('http')
// request获取请求参数对象 response响应对象
const serve = http.createServer((request, response) => {
    let url = request.url
    response.write(url)
    response.end()
})
// 开启监听 三个参数，第一个为端口号，第二个为域名，可省略，第三个为回调
serve.listen(8090, 'localhost', () => {
    console.log('localhost: 8090')
})
// 注: 如果第二步不用变量serve进行接收，可直接进行连写，即链式写法
```

###### 3.fs

```javascript
const fs = require('fs')
fs.writeFile('./test.js', 'let a = 2', (err, data) => {
  // node中的回调错误优先，即第一个形参为错误时的参数
})
```

