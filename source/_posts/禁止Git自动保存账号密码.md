---
title: 禁止Git自动保存账号密码
date: 2018-12-08 17:02:42
categories: git
tags: git
---

默认情况下 git 使用 https 在输入账号密码后会保存到 windows 凭据下。

# 禁止自动保存账号密码
禁止自动保存密码可以修改git的配置文件，system和global配置文件都可以
```
$ git config --global --unset credential.helper

或

$ git config --system --unset credential.helper
```

# 恢复自动保存账号密码

```
$ git config --global credential.helper manager

或

$ git config --system credential.helper manager
```

> (出处https://novnan.github.io/Git/donot-make-git-remember-my-credentials/)