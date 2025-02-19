---
title: Qt信号传递自定义类
tags:
  - Qt
categories:
  - bug记录
poster:
  topic: 标题上方的小字
  headline: 大标题
  caption: 标题下方的小字
  color: 标题颜色
abbrlink: 44138
date: 2025-02-15 00:08:43
updated: 2025-02-15 00:08:43
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

最近在写qt时遇到一个问题
信号传递一个引用自定义参数时，槽函数无法响应，且报错：

```cpp
QObject::connect: Cannot queue arguments of type 'Cards'
(Make sure 'Cards' is registered using qRegisterMetaType().)
```

其中cards为自定义类

### 原因：

**Qt 信号槽机制的底层实现：**

Qt 的信号和槽机制底层是基于事件队列和线程间通信的。当信号发射时，它可能会将参数复制到事件队列中，或者跨线程传递。在跨线程传递信号和槽时，Qt 会尝试将参数序列化，以确保它能够在不同线程间传递。

引用和跨线程
引用（reference） 在内存中直接指向某个对象。当传递一个引用时，实际上并没有复制对象本身，而只是传递了该对象的地址。Qt 无法自动跨线程处理这种类型的参数，尤其是在不同线程之间。

这种行为会导致 `QObject::connect` 无法处理引用类型参数，因为引用无法被安全地序列化或跨线程传递。这就是为什么看到错误提示：

```cpp
QObject::connect: Cannot queue arguments of type 'Cards'。
```

信号参数的队列化
当信号在一个线程发射，并且槽函数在另一个线程中时，Qt 会尝试将信号的参数“队列化”到目标线程中。这意味着：

值传递：Qt 会复制传递给信号的参数，以便它可以安全地传递。
引用传递：由于引用不容易在不同线程之间传递，Qt 会报错，提示无法队列化引用类型。

### 解决办法：

在main函数中加入以下代码：

```cpp
qRegisterMetaType<Cards>("Cards&");//自定义类型注册为 Qt 元对象类型
```

