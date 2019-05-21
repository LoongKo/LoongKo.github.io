---
title: php获取b站up主的相簿
date: 2019-05-21 21:49:23
categories: php
tags:
---
```php
//下载b站up主的相簿
//$uid是up主的uid
//$num是想要下载的数量，若不填写则下载全部(其实是10000*30张，b站up主照片应该不超出这个数量吧，若是超出可以修改下面$i小于的值)
function get_bilibili_album($uid,$num=NULL){
  $count = 0;
  //其实$i可以为无限，因为如果不存在下面会跳出循环，限制了是为了防止比如接口出问题或者改变了等而造成死循环
  //page_size也可以不止30，极限是多少我也不清楚，只是b站页面分页是30
  for ($i=0; $i < 10000; $i++) { 
    $url = 'https://api.vc.bilibili.com/link_draw/v1/doc/doc_list?uid='.$uid.'&page_num='.$i.'&page_size=30&biz=all';
    $json = file_get_contents($url);
    $ret = json_decode($json);
    if ($ret->msg === 'success' && !empty($ret->data->items)) {
      if (!is_dir($uid)) {
        mkdir($uid);
      }
      foreach ($ret->data->items as $key => $value) {
        foreach ($value->pictures as $k => $v) {
          $count++;
          file_put_contents($uid.'/'. $count . '.' . pathinfo($v->img_src,PATHINFO_EXTENSION), file_get_contents($v->img_src));
          if (!empty($num) && $num == ($count)) {
            echo "一共下载{$count}张图片";
            break 3;
          }
        }
      }
    }else{
      echo "一共下载{$count}张图片";
      break;
    }
  }
}
```