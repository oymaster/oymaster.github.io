---
title: linux常用命令
tags: []
categories:
  - 学习记录
  - Linux
poster:
  topic: 标题上方的小字
  headline: 大标题
  caption: 标题下方的小字
  color: 标题颜色
abbrlink: 30335
date: 2025-03-25 10:38:33
updated: 2025-03-25 10:38:33
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



# Linux 命令总结

## 1. 文件操作

| 命令  | 示例                    | 重要参数            | 解释（英文全称）        | 中文解释             | 参数作用                                                   |
| ----- | ----------------------- | ------------------- | ----------------------- | -------------------- | ---------------------------------------------------------- |
| ls    | ls -l /dir              | -l, -a, -h, -t      | List                    | 列出目录内容         | -l: 长格式; -a: 显示隐藏文件; -h: 可读单位; -t: 按时间排序 |
| cd    | cd /home/user           | --                  | Change Directory        | 切换目录             | 无常用参数，直接跟路径即可                                 |
| pwd   | /home/user              | --                  | Print Working Directory | 显示当前工作目录     | 无参数，直接输出当前路径                                   |
| mkdir | mkdir -p /dir/subdir    | -p                  | Make Directory          | 创建目录             | -p: 自动创建父目录（若不存在）                             |
| rm    | rm -rf /dir             | -r, -f              | Remove                  | 删除文件或目录       | -r: 递归删除; -f: 强制删除，不提示                         |
| cp    | cp -r file1 /dir        | -r, -p              | Copy                    | 复制文件或目录       | -r: 递归复制目录; -p: 保留文件属性（如权限、时间戳）       |
| mv    | mv file1 file2          | -i                  | Move                    | 移动或重命名文件     | -i: 覆盖前提示                                             |
| cat   | cat file.txt            | -n                  | Concatenate             | 查看文件内容         | -n: 显示行号                                               |
| touch | touch newfile.txt       | -t                  | Touch                   | 创建空文件或更新时间 | -t: 指定时间戳（如 -t 202301011200）                       |
| find  | find / -name "file.txt" | -name, -type, -size | Find                    | 查找文件             | -name: 按文件名; -type: 文件类型; -size: 按大小（如 +10M） |
| ln    | ln -s file link         | -s                  | Link                    | 创建链接             | -s: 创建符号链接（软链接）                                 |
| stat  | stat file.txt           | --                  | Status                  | 显示文件详细信息     | 无常用参数，显示文件元数据（如权限、大小、时间戳）         |
| file  | file file.txt           | --                  | File                    | 查看文件类型         | 无参数，判断文件类型（如文本、二进制）                     |
| diff  | diff file1 file2        | -u                  | Difference              | 比较文件差异         | -u: 以统一格式输出差异                                     |

## 2. 系统监控

| 命令   | 示例        | 重要参数   | 解释（英文全称）     | 中文解释             | 参数作用                                                     |
| ------ | ----------- | ---------- | -------------------- | -------------------- | ------------------------------------------------------------ |
| top    | top         | -u         | Table of Processes   | 查看实时进程信息     | -u: 指定用户进程（如 -u user）                               |
| htop   | htop        | --         | Hisham's Top         | 更友好的进程查看工具 | 无常用参数，图形化交互界面                                   |
| ps     | ps aux      | aux -ef    | Process Status       | 查看进程状态         | a: 所有终端进程; u: 用户信息; x: 无终端进程; -ef: 完整格式输出 |
| df     | df -h       | -h, -i     | Disk Free            | 查看磁盘空间使用     | -h: 可读单位; -i: 显示 inode 使用情况                        |
| du     | du -sh /dir | -s, -h, -d | Disk Usage           | 查看目录或文件大小   | -s: 总大小; -h: 可读单位; -d: 指定深度（如 -d 1）            |
| free   | free -m     | -m, -t     | Free                 | 查看内存使用情况     | -m: MB 单位; -t: 显示总计行                                  |
| uptime | uptime      | --         | Uptime               | 查看系统运行时间     | 无参数，显示运行时间、用户数和负载                           |
| vmstat | vmstat 1 5  | -s         | Virtual Memory Stats | 查看虚拟内存统计     | -s: 显示内存统计表; 数字参数：采样间隔和次数                 |
| iostat | iostat -x   | -x, -d     | Input/Output Stats   | 查看 I/O 统计        | -x: 扩展统计; -d: 只显示设备统计                             |
| lscpu  | lscpu       | --         | List CPU             | 查看 CPU 信息        | 无参数，显示 CPU 架构、核心数等                              |
| uname  | uname -a    | -a         | Unix Name            | 查看系统信息         | -a: 显示所有信息（如内核版本、主机名）                       |

## 3. 权限管理

| 命令   | 示例                  | 重要参数 | 解释（英文全称） | 中文解释           | 参数作用                                                     |
| ------ | --------------------- | -------- | ---------------- | ------------------ | ------------------------------------------------------------ |
| chmod  | chmod 755 file.sh     | -R       | Change Mode      | 修改文件权限       | -R: 递归更改目录权限                                         |
| chown  | chown user:group file | -R       | Change Owner     | 修改文件所有者     | -R: 递归更改目录所有者                                       |
| sudo   | sudo apt update       | -u       | Superuser Do     | 以超级用户权限执行 | -u: 以指定用户运行（如 -u user）                             |
| whoami | whoami                | --       | Who Am I         | 显示当前用户名     | 无参数，输出当前登录用户名                                   |
| passwd | passwd                | --       | Password         | 修改用户密码       | 无常用参数，交互式输入新密码                                 |
| chgrp  | chgrp group file      | -R       | Change Group     | 修改文件所属组     | -R: 递归更改目录所属组                                       |
| umask  | umask 022             | --       | User Mask        | 设置默认权限掩码   | 无参数，设置新建文件默认权限（如 022 表示新建文件权限为 644） |

## 4. 网络相关

| 命令       | 示例                  | 重要参数       | 解释（英文全称）       | 中文解释           | 参数作用                                           |
| ---------- | --------------------- | -------------- | ---------------------- | ------------------ | -------------------------------------------------- |
| ping       | ping google.com       | -c, -i         | Packet Internet Groper | 测试网络连通性     | -c: 指定包数; -i: 指定发送间隔（如 -i 0.2）        |
| netstat    | netstat -tuln         | -t, -u, -l, -n | Network Statistics     | 查看网络状态       | -t: TCP; -u: UDP; -l: 监听端口; -n: 数字格式       |
| curl       | curl -O url           | -O, -I         | Client URL             | 下载或请求网页数据 | -O: 下载文件; -I: 只返回头部信息                   |
| wget       | wget -r url           | -r             | Web Get                | 下载文件           | -r: 递归下载网站内容                               |
| ifconfig   | ifconfig eth0 up      | up, down       | Interface Config       | 配置网络接口       | up: 启用接口; down: 禁用接口                       |
| ssh        | ssh user@host         | -p, -i         | Secure Shell           | 远程登录           | -p: 指定端口; -i: 指定私钥文件（如 -i ~/.ssh/key） |
| traceroute | traceroute google.com | -n             | Trace Route            | 跟踪路由路径       | -n: 不解析主机名，仅显示 IP                        |
| nc         | nc -zv host 80        | -z, -v         | Netcat                 | 网络调试工具       | -z: 扫描端口; -v: 显示详细信息                     |
| ip         | ip addr show          | addr, link     | IP                     | 查看或配置网络     | addr: 显示地址; link: 显示接口状态                 |
| ss         | ss -tuln              | -t, -u, -l, -n | Socket Statistics      | 查看套接字状态     | -t: TCP; -u: UDP; -l: 监听; -n: 数字格式           |

## 5. 进程管理

| 命令    | 示例                  | 重要参数 | 解释（英文全称） | 中文解释           | 参数作用                                        |
| ------- | --------------------- | -------- | ---------------- | ------------------ | ----------------------------------------------- |
| kill    | kill -9 1234          | -9, -15  | Kill             | 终止进程           | -9: SIGKILL 强制终止; -15: SIGTERM 优雅终止     |
| pkill   | pkill -f process_name | -f, -u   | Process Kill     | 按名称终止进程     | -f: 按命令名匹配; -u: 按用户终止（如 -u user）  |
| nohup   | nohup script.sh &     | --       | No Hang Up       | 后台运行不挂断     | 无参数，配合 & 在终端关闭后继续运行             |
| jobs    | jobs                  | -l       | Jobs             | 查看后台任务       | -l: 显示进程 ID                                 |
| bg      | bg %1                 | --       | Background       | 将任务放入后台     | 无参数，配合任务编号（如 %1）                   |
| fg      | fg %1                 | --       | Foreground       | 将任务调回前台     | 无参数，配合任务编号（如 %1）                   |
| nice    | nice -n 10 command    | -n       | Nice             | 设置进程优先级     | -n: 指定优先级值（-20 到 19，值越低优先级越高） |
| renice  | renice 10 -p 1234     | -p       | Renice           | 修改运行进程优先级 | -p: 指定进程 ID                                 |
| killall | killall httpd         | -i       | Kill All         | 按名称杀死所有进程 | -i: 交互式确认                                  |

## 6. 文件内容操作

| 命令 | 示例                   | 重要参数   | 解释（英文全称）                | 中文解释       | 参数作用                                          |
| ---- | ---------------------- | ---------- | ------------------------------- | -------------- | ------------------------------------------------- |
| grep | grep -r "text" /dir    | -i, -r, -n | Global Regular Expression Print | 搜索文件内容   | -i: 忽略大小写; -r: 递归搜索; -n: 显示行号        |
| sed  | sed 's/old/new/g' file | -i         | Stream Editor                   | 流编辑器       | -i: 直接修改文件                                  |
| awk  | awk '{print $1}' file  | -F         | Aho, Weinberger, Kernighan      | 文本处理工具   | -F: 指定分隔符（如 -F: 以冒号分隔）               |
| head | head -n 5 file.txt     | -n         | Head                            | 显示文件头部   | -n: 指定行数（如 -n 5）                           |
| tail | tail -n 5 file.txt     | -n, -f     | Tail                            | 显示文件尾部   | -n: 指定行数; -f: 实时跟踪                        |
| less | less file.txt          | -N         | Less                            | 分页查看文件   | -N: 显示行号                                      |
| wc   | wc -l file.txt         | -l, -w, -c | Word Count                      | 统计行数、字数 | -l: 行数; -w: 单词数; -c: 字符数                  |
| cut  | cut -d: -f1 file.txt   | -d, -f     | Cut                             | 按字段截取文本 | -d: 指定分隔符; -f: 指定字段（如 -f1 表示第一列） |
| sort | sort file.txt          | -r, -n     | Sort                            | 排序文件内容   | -r: 逆序; -n: 按数值排序                          |
| uniq | uniq file.txt          | -c         | Unique                          | 去除重复行     | -c: 显示每行重复次数                              |

## 7. 压缩与解压

| 命令   | 示例                       | 重要参数       | 解释（英文全称）    | 中文解释        | 参数作用                                              |
| ------ | -------------------------- | -------------- | ------------------- | --------------- | ----------------------------------------------------- |
| tar    | tar -czvf file.tar.gz /dir | -c, -z, -v, -f | Tape Archive        | 打包与解包      | -c: 创建; -z: gzip 压缩; -v: 显示过程; -f: 指定文件名 |
| gzip   | gzip file.txt              | -d             | GNU Zip             | 压缩文件        | -d: 解压（等同 gunzip）                               |
| gunzip | gunzip file.txt.gz         | --             | GNU Unzip           | 解压文件        | 无常用参数，解压 .gz 文件                             |
| zip    | zip -r file.zip /dir       | -r             | Zip                 | 压缩为 zip 格式 | -r: 递归压缩目录                                      |
| unzip  | unzip file.zip             | -l             | Unzip               | 解压 zip 文件   | -l: 仅列出文件内容，不解压                            |
| bzip2  | bzip2 file.txt             | -d             | Burrows-Wheeler Zip | 更高压缩比      | -d: 解压（等同 bunzip2）                              |

## 8. 软件管理

| 命令 | 示例                 | 重要参数         | 解释（英文全称）           | 中文解释        | 参数作用                           |
| ---- | -------------------- | ---------------- | -------------------------- | --------------- | ---------------------------------- |
| apt  | apt install package  | install, remove  | Advanced Package Tool      | Debian 系包管理 | install: 安装; remove: 删除软件包  |
| yum  | yum install package  | install, update  | Yellowdog Updater Modified | CentOS 包管理   | install: 安装; update: 更新软件包  |
| dpkg | dpkg -i package.deb  | -i, -r           | Debian Package             | 安装 deb 包     | -i: 安装; -r: 删除                 |
| rpm  | rpm -ivh package.rpm | -i, -v, -h       | Red Hat Package Manager    | 安装 rpm 包     | -i: 安装; -v: 详细信息; -h: 进度条 |
| snap | snap install package | --classic        | Snap                       | 安装 snap 包    | --classic: 允许访问系统资源        |
| dnf  | dnf install package  | install, upgrade | Dandified Yum              | Fedora 包管理   | install: 安装; upgrade: 升级所有包 |

## 9. 日志查看

| 命令       | 示例                  | 重要参数   | 解释（英文全称） | 中文解释           | 参数作用                                 |
| ---------- | --------------------- | ---------- | ---------------- | ------------------ | ---------------------------------------- |
| journalctl | journalctl -u service | -u, -f, -n | Journal Control  | 查看系统日志       | -u: 服务日志; -f: 实时跟踪; -n: 指定行数 |
| dmesg      | dmesg                 | grep error | -T               | Diagnostic Message | 查看内核日志                             |
| last       | last -x               | -x         | Last             | 查看登录历史       | -x: 显示系统事件（如关机、重启）         |
| logrotate  | logrotate -f config   | -f         | Log Rotate       | 轮转日志文件       | -f: 强制执行轮转                         |

## 10. 环境变量管理

| 命令   | 示例             | 重要参数 | 解释（英文全称） | 中文解释     | 参数作用                          |
| ------ | ---------------- | -------- | ---------------- | ------------ | --------------------------------- |
| env    | env              | --       | Environment      | 查看环境变量 | 无参数，列出所有环境变量          |
| export | export VAR=value | --       | Export           | 设置环境变量 | 无参数，设置并导出变量到子进程    |
| unset  | unset VAR        | --       | Unset            | 删除环境变量 | 无参数，移除指定变量              |
| set    | set              | --       | Set              | 查看所有变量 | 无参数，显示环境变量和 shell 函数 |

## 11. 用户管理

| 命令     | 示例                   | 重要参数 | 解释（英文全称） | 中文解释     | 参数作用                                          |
| -------- | ---------------------- | -------- | ---------------- | ------------ | ------------------------------------------------- |
| useradd  | useradd -m user        | -m, -s   | User Add         | 添加用户     | -m: 创建家目录; -s: 指定 shell（如 -s /bin/bash） |
| usermod  | usermod -aG group user | -aG      | User Modify      | 修改用户信息 | -aG: 添加用户到组（附加，不覆盖）                 |
| userdel  | userdel -r user        | -r       | User Delete      | 删除用户     | -r: 删除用户及其家目录                            |
| groupadd | groupadd group         | --       | Group Add        | 添加用户组   | 无常用参数，直接创建组                            |
| id       | id user                | --       | Identity         | 查看用户身份 | 无参数，显示用户 UID、GID 和组信息                |

## 12. 磁盘管理

| 命令   | 示例                 | 重要参数 | 解释（英文全称） | 中文解释       | 参数作用                                |
| ------ | -------------------- | -------- | ---------------- | -------------- | --------------------------------------- |
| fdisk  | fdisk /dev/sda       | -l       | Fixed Disk       | 管理磁盘分区   | -l: 列出分区表                          |
| mkfs   | mkfs.ext4 /dev/sda1  | --       | Make Filesystem  | 格式化文件系统 | 无常用参数，指定文件系统类型（如 ext4） |
| mount  | mount /dev/sda1 /mnt | -t       | Mount            | 挂载文件系统   | -t: 指定文件系统类型（如 -t ext4）      |
| umount | umount /mnt          | --       | Unmount          | 卸载文件系统   | 无常用参数，直接卸载挂载点              |
| lsblk  | lsblk                | -f       | List Block       | 列出块设备     | -f: 显示文件系统类型和挂载点            |

## 13. 任务调度

| 命令  | 示例            | 重要参数 | 解释（英文全称） | 中文解释     | 参数作用                                |
| ----- | --------------- | -------- | ---------------- | ------------ | --------------------------------------- |
| cron  | crontab -e      | -e, -l   | Command Run On   | 定时任务     | -e: 编辑任务; -l: 列出任务              |
| at    | at now + 1 hour | --       | At               | 单次定时任务 | 无参数，指定执行时间（如 now + 1 hour） |
| batch | batch           | --       | Batch            | 批量任务     | 无参数，在系统负载低时执行              |

## 14. 性能分析

| 命令   | 示例              | 重要参数     | 解释（英文全称）       | 中文解释     | 参数作用                                   |
| ------ | ----------------- | ------------ | ---------------------- | ------------ | ------------------------------------------ |
| strace | strace -p 1234    | -p, -o       | System Trace           | 跟踪系统调用 | -p: 指定进程 ID; -o: 输出到文件            |
| lsof   | lsof -p 1234      | -p, -i       | List Open Files        | 列出打开文件 | -p: 指定进程; -i: 显示网络文件             |
| perf   | perf stat command | stat, record | Performance            | 性能分析     | stat: 统计性能; record: 记录数据           |
| sar    | sar -u 1 5        | -u           | System Activity Report | 系统活动报告 | -u: CPU 使用情况; 数字参数：采样间隔和次数 |

