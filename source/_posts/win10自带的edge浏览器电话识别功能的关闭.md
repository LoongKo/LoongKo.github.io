---
title: win10自带的edge浏览器电话识别功能的关闭
date: 2019-05-21 21:06:36
categories: html
tags:
---
win10自带的edge浏览器默认会把电话号码识别功能打开，即使不是电话号码类似电话号码也会识别成电话号码，看起来像是超链接一样，但是很多时候我们并不需要这样的功能，下面介绍两种关闭的方法。

方法一：在`head`加入
`<meta name="format-detection" content="telephone=no"/>`

方法二：在想要停用电话识别的元素设置`x-ms-format-detection`为`none`，比如：
`<div x-ms-format-detection='none'></div>`

> 出处：[微软官方文档](https://docs.microsoft.com/zh-cn/previous-versions/windows/internet-explorer/ie-developer/dev-guides/dn265018(v=vs.85&#41;)