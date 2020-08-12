---
title: nodejs开启http服务器
date: 2020-08-13 01:10:48
categories:
tags:
---
# 开启http服务器作为文件转发
```js
const http = require('http');
const request = require('request')
const url = require('url');

function getClientIp(req) {
        return req.headers['x-forwarded-for'] ||
        req.connection.remoteAddress ||
        req.socket.remoteAddress ||
        req.connection.socket.remoteAddress;
}

http.createServer({'trust proxy': true},function(req, res){
  let params = url.parse(req.url, true).query
  //params为获取的请求参数
  if (params.download) {
    res.writeHead(200, {'Content-Type': 'image/jpeg', 'Content-Disposition':'attachment; filename="'+(new Date().getTime())+'.jpg"'});
    console.log('['+getClientIp(req)+']' + params.download)
    request(params.download).pipe(res)
  }else{
    console.log('['+getClientIp(req)+']'+JSON.stringify(params))
    res.end('error')
  }
}).listen(4000);
```

直接访问`http://127.0.0.1:4000`即可访问。

# 开启服务器
```js
var http = require('http');
http.createServer(function (request, response) {
    // 发送 HTTP 头部 
    // HTTP 状态值: 200 : OK
    // 内容类型: text/plain
    response.writeHead(200, {'Content-Type': 'text/plain'});

    // 发送响应数据 "Hello"
    response.write("Hello");
    response.end();
}).listen(4000);
```
```js
var http = require('http');
http.createServer(function (request, response) {
    // 发送 HTTP 头部 
    // HTTP 状态值: 200 : OK
    // 内容类型: text/plain
    response.writeHead(200, {'Content-Type': 'text/plain'});

    // 发送响应数据 "Hello"
    response.end("hello");
}).listen(4000);
```
直接访问`http://127.0.0.1:4000`即可访问。