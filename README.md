goweb 随启随用的静态文件服务器
==============================

Running static file server anywhere. 随时随地将你的当前目录变成一个静态文件服务器的根目录。

## Installation

Install it as a command line tool via `npm -g`.

```sh
npm install goweb -g
```

## Execution

```sh
$ goweb
// or with port
$ goweb -p 8000
// or start it but silent(don't open browser)
$ goweb -s
// or with hostname
$ goweb -h localhost -p 8888
// or with folder
$ goweb -d ~/git/goweb
// or enable html5 history
$ goweb -f /index.html
```

## Help

```sh
$ goweb --help
Usage:
  goweb --help // print help information
  goweb // 8000 as default port, current folder as root
  goweb 8888 // 8888 as port
  goweb -p 8989 // 8989 as port
  goweb -s // don't open browser
  goweb -h localhost // localhost as hostname
  goweb -d /home // /home as root
  goweb -f /index.html  // Enable html5 history,the index is /index.html
  goweb --proxy http://localhost:7000/api // Support shorthand URL, webpack.config.js or customize config file
```

#### Proxy argvs

**Shorthand URL**
```
goweb --proxy http://localhost:7000/api
                 \___________________/\___/
                              |         |
                           target    context
```
More about the [shorthand configuration](https://github.com/chimurai/http-proxy-middleware#shorthand).

**Webpack conofig**
```javascript
// webpack.conofig.js
module.exports = {
  devServer: {
    proxy: {
      '/api': {
        target: 'http://localhost:7000',
        changeOrigin: true
      }
    }
  }
}
```

**Customize config**
```javascript
// proxy.config.js
module.exports = {
  '/api': {
    target: 'http://localhost:7000',
    changeOrigin: true
  }
}
```
More proxy [http-proxy-middleware](https://github.com/chimurai/http-proxy-middleware#context-matching) help.

## Visit

```
http://localhost:8000
```
Automatically open default browser. 执行命令后，默认浏览器将为您自动打开主页。

## License
The MIT license.
