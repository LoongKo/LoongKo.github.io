---
title: PHP删除指定目录的函数
date: 2018-10-24 01:45:03
categories: php
tags: php
---

```php
/**
 * 删除指定目录的函数（包括子文件夹和子文件夹里面的文件，也就是说删除整个目录）
 * 递归删除
 * $dir为指定文件夹的绝对路径
 */
function del_dir($dir){
   if ($handle = opendir($dir)){
     while (false !== ($item = readdir($handle))){
       if ($item != '.' && $item != '..'){
         if (is_dir($dir . '/' . $item)){
           del_dir($dir . '/' . $item);
         }
         else{
           unlink($dir . '/' . $item);
         }
       }
     }
     closedir($handle);
     rmdir($dir);
   }
}
```