---
title: php写文件
date: 2020-08-13 00:44:03
categories: php
tags: php
---
# php写入文件(覆盖)

```php
file_put_contents('./test.txt', 'hello');

```

# php写入文件(追加)
```php
file_put_contents('./test.txt', 'hello', FILE_APPEND | LOCK_EX);

```