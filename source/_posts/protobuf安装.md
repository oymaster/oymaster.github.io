---
title: protobuf安装
tags:
  - ProtoBuf
categories:
  - 学习记录
  - 数据序列化
poster:
  topic: 标题上方的小字
  headline: 大标题
  caption: 标题下方的小字
  color: 标题颜色
abbrlink: 32845
date: 2025-02-27 17:02:37
updated: 2025-02-27 17:02:37
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

## 安装

github官方链接 https://github.com/protocolbuffers/protobuf/

以protobuf21为例 https://github.com/protocolbuffers/protobuf/releases/download/v21.11/protobuf-all-21.11.zip

### windows

1. 解压好文件夹后,使用cmake,vs,qt creator等工具打开该项目,进行编译,编译需要注意下面三个地方,测试部分可以取消掉,节省时间

![image-20250227175029890](https://pub-e575a4be91854c8e8b675e7e977ed21f.r2.dev/image-20250227175029890.png)

2. 编译完成后,进入build文件夹中,通常有以下文件`protoc.exe`,`libprotobuf.dll`,`libproto.dll`,一个可执行文件和两个动态库,如果是debug模式下这两个动态库为`libprotobufd.dll`,`libprotod.dll`

3. 选择一个合适的路径,创建如下三个文件夹,将`protoc.exe`放入bin目录,`libprotobuf.dll`,`libproto.dll`放入lib目录

<img src="https://pub-e575a4be91854c8e8b675e7e977ed21f.r2.dev/image-20250227175521242.png" alt="image-20250227175521242" style="zoom:67%;" />

4. 将前面下载解压后的protobuf-all-21.11.zip中的protobuf-3.21.11\src\google目录，将google拖入上面的include中即可

5. 添加两个系统环境变量，一个bin，一个lib，刷新变量后，使用

   ```shell
   protoc --version
   ```

   出现版本号便可以了

### linux

以同样的版本为例，用https://github.com/protocolbuffers/protobuf/releases/download/v21.11/protobuf-all-21.11.tar.gz

1. 解压后进入目录，执行以下命令：

   ```shell
   ./configure
   make
   sudo make install 
   ```

2. 如果期间出现报错，如动态库无法找到，可以利用find命令查找该动态库，然后将该路径添加到/etc/ld.so.conf

3. 最后执行：

   ```shell
   protoc --version
   ```

   出现版本号便可以了





