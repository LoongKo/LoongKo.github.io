---
title: Browsersync简单使用说明
date: 2019-05-30 21:20:42
categories: 其他
tags: 
---
[Browsersync](http://www.browsersync.cn/)是一个同步测试工具，能实现自动刷新，比如我修改html,css,js等文件，保存了之后浏览器会自动刷新页面，各个页面也能同步，当然监控什么类型文件都可以设置，主要记录一下我常用的。

# 安装Browsersync(全局安装)
`npm install -g browser-sync`

# 启动Browsersync
启动本地服务器并监控当前目录下所有文件，更多命令可查看[官方文档](http://www.browsersync.cn/docs/command-line/)
`browser-sync start --server --files '**'`