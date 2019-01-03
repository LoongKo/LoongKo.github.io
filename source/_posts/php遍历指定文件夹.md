---
title: php遍历指定文件夹
date: 2018-11-26 21:38:11
categories: php
tags: php
---

```php
//遍历指定文件夹
// $path为文件夹路径
function get_all_files($path){
  $list = array();
  foreach(glob($path . '/*') as $item){
    if(is_dir($item)){
     $list = array_merge($list , get_all_files($item));
    }
    else{
     $list[] = $item;
    }
  }
  return $list;
}
```
