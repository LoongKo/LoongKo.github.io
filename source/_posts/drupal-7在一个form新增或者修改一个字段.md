---
title: drupal 7在一个form新增或者修改一个字段
date: 2018-10-21 17:47:33
categories: drupal
tags:
---
例如在以下页面新增一个工号字段

{% asset_img 1.png %}

在模块文件里面通过`hook_form_FORM_ID_alter`函数修改，比如

<!-- more -->

{% asset_img 2.png %}

图中的helloworld是模块名称，也就是你在哪个模块里面写这个函数那么名称就是什么（此例子在helloworld.module写的），user_register_form是你要修改或者新增的form的id，注意是form的id，通过浏览器的开发者工具可以看到。

{% asset_img 3.png %}

也就是说格式为模块名form要修改form的id_alter。修改后如下图：

{% asset_img 4.png %}

可以用`hook_form_alter`函数也可以，这个可以修改多个form，例如可以通过if语句判断form的id，来确定要修改哪个form。
