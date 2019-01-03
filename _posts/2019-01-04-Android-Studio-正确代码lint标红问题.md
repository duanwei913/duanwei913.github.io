---
layout:     post
title:      "爬坑: Android Studio 正确代码被lint标红问题"
date:       2019-01-03 08:00:00
author:     "段胖子"
header-img: "img/post-bg-2015.jpg"
tags:
    - Android开发
    - 坑
---

## 问题背景
早上打开Android Studio的时候，发现正常的support.v4库里的很多代码全部被标红。显示Cannot resolve symbol Fragment等奇怪的lint提示。

经过反复面向Google编程，先后采用了以下方法：
1. Clean Project
2. Rebuild Project
3. Sync Project With Gradle Files ( 在MacOS下，这个选项在File菜单下 )
4. Invalidate Cache / Restart ( 同样在MacOS下，这个选项在File菜单下 )

当然，这些办法全都不好使。

## 解决办法
参考[StackOverflow](https://stackoverflow.com/questions/20386331/android-studio-and-android-support-v4-app-fragment-cannot-resolve-symbol)上这个和我的症状非常像的哥们，采用了下面这个方法：
删除 项目路径/.idea/library/ 目录，然后再Sync Project With Gradle Files

问题解决。

## 总结
看起来还是Android Studio的一个Bug，本地缓存干扰了正常的Lint工作。
