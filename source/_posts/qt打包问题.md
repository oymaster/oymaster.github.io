---
title: Qt报错：无法定位程序输入点于动态链接库
tags:
  - Qt
categories:
  - bug记录
poster:
  topic: 标题上方的小字
  headline: 大标题
  caption: 标题下方的小字
  color: 标题颜色
abbrlink: 984
date: 2025-02-19 21:41:53
updated: 2025-02-19 21:41:53
description:
cover:
banner:
sticky:
mermaid:
katex:
mathjax:
topic:
author:
references:
comments:
indexing:
breadcrumb:
leftbar:
rightbar:
h1:
type:
---


### 问题描述：

qt程序在编译release版本后正常运行，进入release下面的文件夹执行.exe会报错：**无法定位程序输入点于动态链接库**

### 原因：

系统环境变量中，Anaconda的mingw变量在前面冲突了

### 解决办法：

找到该项目的编译器路径，在环境变量->系统变量中将该编译器路径放在其他mingw上方，通过上移操作即可
