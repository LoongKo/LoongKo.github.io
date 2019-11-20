---
title: git导出变更的文件
date: 2019-11-20 23:37:34
categories: git
tags: git
---
git导出变更的文件，把下面的`commit_id`改为真实具体的，后面的`update.tar`是文件名。
```
git diff commit_id --name-only | xargs tar -cvf update.tar
```