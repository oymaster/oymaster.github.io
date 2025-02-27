---
title: redis常用命令
tags:
  - Redis
categories:
  - 学习记录
  - 数据库
poster:
  topic: 标题上方的小字
  headline: 大标题
  caption: 标题下方的小字
  color: 标题颜色
abbrlink: 34206
date: 2025-02-27 17:19:46
updated: 2025-02-27 17:19:46
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



## 个人理解

一个大号的Map

## 安装

github官网下载https://github.com/redis/redis/archive/refs/tags/7.4.2.tar.gz

解压后执行：

```shell
make
sudo make install
```

启动服务端:

```shell
redis-server
```

默认端口是6379

启动客户端

```shell
redis-cli
```

## 命令

### **1. 字符串（String）**
字符串是最基础的数据类型，适合存单个值，比如计数、缓存数据。

- **`SET` - 设置键值**
  - **用法**：`SET key value`
  - **例子**：`SET user "张三"`  
  - **场景**：存用户名。
  
- **`GET` - 获取值**
  - **用法**：`GET key`
  - **例子**：`GET user`  
  - **场景**：读取用户名。
  
- **`INCR` - 自增 1**
  - **用法**：`INCR key`
  - **例子**：`INCR views`  
  - **场景**：统计页面访问量。
  
- **`DEL` - 删除键**
  - **用法**：`DEL key`
  - **例子**：`DEL user`  
  - **场景**：清理无用数据。

### **2. 列表（List）**

列表是有序的队列，可以从两端操作，适合存顺序数据。

- **`LPUSH` - 从左侧插入**
  - **用法**：`LPUSH key value`
  - **例子**：`LPUSH tasks "写代码"`  结果：`tasks` 列表变成 `["写代码"]`。
  - **场景**：添加新任务。
  
- **`RPUSH` - 从右侧插入**
  - **用法**：`RPUSH key value`
  - **例子**：`RPUSH tasks "开会"`  结果：`tasks` 变成 `["写代码", "开会"]`。
  - **场景**：追加消息。
  
- **`LPOP` - 从左侧弹出**
  - **用法**：`LPOP key`
  - **例子**：`LPOP tasks`  返回：“写代码”，剩 `["开会"]`。
  - **场景**：完成任务。
  
- **`LRANGE` - 获取范围元素**
  - **用法**：`LRANGE key start stop`
  - **例子**：`LRANGE tasks 0 -1`  返回：`["开会"]`（全部元素）。
  - **场景**：查看任务列表。

### **3. 集合（Set）**
集合是无序、不重复的元素集合，适合去重或关系操作。

- **`SADD` - 添加元素**
  - **用法**：`SADD key member`
  - **例子**：`SADD friends "小明" "小红"`  结果：`friends` 集合是 `{"小明", "小红"}`。
  - **场景**：添加好友。
  
- **`SMEMBERS` - 获取所有元素**
  - **用法**：`SMEMBERS key`
  - **例子**：`SMEMBERS friends`  返回：`["小明", "小红"]`。
  - **场景**：列出所有好友。
  
- **`SREM` - 删除元素**
  - **用法**：`SREM key member`
  - **例子**：`SREM friends "小明"`  结果：剩 `{"小红"}`。
  - **场景**：删除好友。
  
- **`SINTER` - 求交集**
  - **用法**：`SINTER key1 key2`
  - **例子**：`SINTER friends colleagues`  返回：`["小红"]`（假设 `colleagues` 有“小红”“小刚”）。
  - **场景**：找共同好友。

### **4. 哈希（Hash）**
哈希像一个小表格，适合存结构化数据，比如对象。

- **`HSET` - 设置字段值**
  - **用法**：`HSET key field value`
  - **例子**：`HSET user:001 name "张三" age "25"`  结果：`user:001` 是 `{name: "张三", age: "25"}`。
  - **场景**：存用户信息。
  
- **`HGET` - 获取字段值**
  - **用法**：`HGET key field`
  - **例子**：`HGET user:001 name`  返回：“张三”。
  - **场景**：读取姓名。
  
- **`HGETALL` - 获取所有字段和值**
  - **用法**：`HGETALL key`
  - **例子**：`HGETALL user:001`  返回：`{name: "张三", age: "25"}`。
  - **场景**：显示用户详情。
  
- **`HDEL` - 删除字段**
  - **用法**：`HDEL key field`
  - **例子**：`HDEL user:001 age`  结果：剩 `{name: "张三"}`。
  - **场景**：删除年龄信息。



