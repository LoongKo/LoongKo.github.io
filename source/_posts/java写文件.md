---
title: java写文件
date: 2020-08-13 00:46:43
categories: java
tags: java
---
# java写文件(覆盖)
```java
import java.io.*;

public class test{
  public static void main(String[] args) throws IOException {
    FileWriter writer = new FileWriter("./test.txt", false);
    writer.write("hello");
    writer.flush();
    writer.close();
  }
}
```

# java写文件(追加)
```java
import java.io.*;

public class test{
  public static void main(String[] args) throws IOException {
    FileWriter writer = new FileWriter("./test.txt", true);
    writer.write("hello");
    writer.flush();
    writer.close();
  }
}
```