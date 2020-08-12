---
title: python写文件
date: 2020-08-13 00:46:29
categories: python
tags: python
---
# python写文件(覆盖)
```python
with open('./test.txt',"w", encoding="utf-8") as file:
    file.write('hello')
```

# python写文件(追加)
```python
with open('./test.txt',"a", encoding="utf-8") as file:
    file.write('hello')
```
