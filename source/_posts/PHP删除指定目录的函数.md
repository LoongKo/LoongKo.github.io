---
title: PHP删除指定目录的函数
date: 2018-10-24 01:45:03
categories: php
tags: php
---

网上找的，忘了出处了。

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

还有一种方法是使用`glob`函数(自己写的)

```php
/**
 * 删除指定目录的函数（包括子文件夹和子文件夹里面的文件，也就是说删除整个目录）
 * 递归删除
 * $path为指定文件夹的绝对路径
 */
function delete_dir($path){
  $file_arr = glob($path . '/*');
  foreach ($file_arr as $value) {
    if (is_dir($value)) {
      delete_dir($value);
    }else{
      unlink($value);
    }
    $dir = dirname($value);
    if (empty(glob($dir.'/*'))) {
      rmdir($dir);
    }
  }
  if (empty($file_arr)) {
    rmdir($path);
  }
}
```