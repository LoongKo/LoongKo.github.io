---
title: php把远程图片保存到本地文件夹
date: 2019-04-15 13:49:57
categories: php
tags: php
---
php把远程的图片保存到本地文件夹的小栗子
```php
$imgpath = 'https://avatars0.githubusercontent.com/u/20168685?s=460&v=4';
file_put_contents('saveimg.jpg', file_get_contents($imgpath));
```
通过这样结合[DomCrawler](https://symfony.com/doc/current/components/dom_crawler.html)可以爬取网站的一些图片下来的。
自己测试了一下爬取3600多张大概用了14分钟，每张20KB左右的大小，当然没用多线程的方式只是单线程，也没怎么考虑优化，只是大概测试一下，仅供参考。

同理除了图片其他文件也是可以的。