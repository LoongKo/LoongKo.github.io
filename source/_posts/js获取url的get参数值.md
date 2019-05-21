---
title: js获取url的get参数值
date: 2019-05-21 21:19:18
categories: js
tags:
---
```js
function GetQueryString(name){
  var reg = new RegExp("(^|\\?|&)" + name + "=([^&]*)(\\s|&|$)","i");
  if(reg.test(window.location.href)){
    return decodeURIComponent(RegExp.$2.replace(/\+/g," "))
  }else{
    return false;
  }
}
```