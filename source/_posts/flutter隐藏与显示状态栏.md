---
title: flutter隐藏与显示状态栏
date: 2019-04-12 18:02:45
categories: flutter
tags: flutter
---
# 引入所需的包
```dart
import 'package:flutter/services.dart';
```

# 隐藏状态栏
```dart
SystemChrome.setEnabledSystemUIOverlays([]);
```

# 显示状态栏
```dart
SystemChrome.setEnabledSystemUIOverlays(SystemUiOverlay.values);
```
