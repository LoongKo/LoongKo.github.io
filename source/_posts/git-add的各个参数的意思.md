---
title: git add的各个参数的意思
date: 2018-10-22 19:55:45
categories: git
tags: git
---
今天在网上搜索了一下`git add .`和`git add -u`以及`git add -A`的区别是什么,找到很多的资料都是说

git add . 提交新文件和修改的文件，不包括被删除的文件
git add -u 提交修改和被删除的文件，不包括新文件
git add -A 提交所有文件

但是我测试之后发现其实`git add .`和`git add -A`效果是一样的，都是提交所有文件
<!-- more -->
后来我在stackoverflow搜索了一下发现原来是版本问题，上面的我原先搜索到的答案其实是对应git 1.x的版本的，我自己测试的时候是git 2.x版本。

** 所以对于`git add`的参数正确的答案如下图所示 **

** Git Version 1.x: ** 
{% asset_img 1.jpg %}

** Git Version 2.x: **
{% asset_img 2.jpg %}

参考资料https://stackoverflow.com/questions/572549/difference-between-git-add-a-and-git-add