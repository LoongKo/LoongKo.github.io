---
title: flutter强制横屏和竖屏
date: 2019-04-12 18:06:51
categories: flutter
tags: fluter
---
记得先引入所需的包，另外貌似以下方法在ios上无效(本人未在ios上验证，android可以)。

# 引入所需的包
```dart
import 'package:flutter/services.dart';
```

# 强制横屏
```dart
SystemChrome.setPreferredOrientations([
  DeviceOrientation.landscapeLeft,
  DeviceOrientation.landscapeRight
]);
```

# 强制竖屏
```dart
SystemChrome.setPreferredOrientations([
  DeviceOrientation.portraitUp,
  DeviceOrientation.portraitDown
]);
```

# 默认
```dart
SystemChrome.setPreferredOrientations([]);
```