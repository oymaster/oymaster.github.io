---
title: Ubuntu 20.04 + mysql 8 默认密码问题
tags:
  - MySQL
categories:
  - bug记录
poster:
  topic: 标题上方的小字
  headline: 大标题
  caption: 标题下方的小字
  color: 标题颜色
abbrlink: 44849
date: 2025-02-28 00:04:31
updated: 2025-02-28 00:04:31
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

Ubuntu20.04安装完mysql8之后无法登录，不知道密码

```shell
mysql -u root 
```

### 原因：

系统默认自动配置好了用户和强密码

### 解决办法：

```shell
sudo cat /etc/mysql/debian.cnf
```

查看该文件

![image-20250228001017290](https://pub-e575a4be91854c8e8b675e7e977ed21f.r2.dev/image-20250228001017290.png)

利用上面的user 和 passwd 即可登录mysql

```cpp
mysql -u(user) -p(passwd) 
```

随后修改密码

进入mysql后执行以下命令：

```shell
use mysql; 
 
update user set authentication_string='' where user='root';      
 
alter user 'root'@'localhost' identified with mysql_native_password by 'xxx';     #修改密码为xxx
```

退出后即可正常登录

```shell
mysql -u root -p 
```

