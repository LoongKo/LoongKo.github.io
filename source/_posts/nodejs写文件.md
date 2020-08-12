---
title: nodejs写文件
date: 2020-08-13 00:46:16
categories: nodejs
tags: nodejs
---
# nodejs写文件(异步)
```js
const fs = require('fs')
fs.appendFile('./test.txt', 'hello', function(error){
    
})
```
# nodejs写文件(同步)
```js
const fs = require('fs')
fs.appendFileSync('./test.txt', 'hello', function(error){//异步
      
})
```