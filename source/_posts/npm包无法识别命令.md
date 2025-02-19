---
title: npm包无法识别命令
tags:
  - npm
categories:
  - bug记录
poster:
  topic: 标题上方的小字
  headline: 大标题
  caption: 标题下方的小字
  color: 标题颜色
abbrlink: 37904
date: 2025-02-19 21:54:42
updated: 2025-02-19 21:54:42
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

今天hexo新文章时，无法找到hexo命令，明明昨天还好好的，突然npm下的包都无法识别命令了。node版本如下：

![image-20250219215632508](https://pub-e575a4be91854c8e8b675e7e977ed21f.r2.dev/image-20250219215632508.png)

### 原因：

环境变量没配好，去查看npm的变量时，它的路径是**C:\Users\*\AppData\Roaming\npm**，进入文件夹啥也没有

### 解决办法：

使用`npm config get prefix` 找到当前包目录，添加到系统变量中即可

![image-20250219220257078](https://pub-e575a4be91854c8e8b675e7e977ed21f.r2.dev/image-20250219220257078.png)

![image-20250219220451100](https://pub-e575a4be91854c8e8b675e7e977ed21f.r2.dev/image-20250219220451100.png)
