---
title: git add status中文文件名乱码解决方法
date: 2019-01-03 23:10:00
categories: git
tags: git
---
配置`core.quotepath`为`false`

例如设置全局的

```
git config --global core.quotepath false
```

当然你也可以不设置`global`而是设置`system`或者`local`