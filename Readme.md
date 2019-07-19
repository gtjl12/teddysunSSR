usage:

wget --no-check-certificate -O shadowsocks-all.sh https://raw.githubusercontent.com/speedyworldclub/tsun55R/shadowsocks-all.sh

chmod +x shadowsocks-all.sh

./shadowsocks-all.sh 2>&1 | tee shadowsocks-all.log



![Shadowsocks](https://github.com/teddysun/shadowsocks_install/raw/master/shadowsocks.png)
# Auto install Shadowsocks Server

shadowsocks.sh
===============
- Auto Install Shadowsocks(Python) Server for CentOS/Debian/Ubuntu
- https://teddysun.com/342.html

shadowsocks-libev.sh
===============
- Auto Install Shadowsocks(libev) Server for CentOS
- https://teddysun.com/357.html

shadowsocks-libev-debian.sh
===============
- Auto Install Shadowsocks(libev) Server for Debian/Ubuntu
- https://teddysun.com/358.html

shadowsocks-go.sh
===============
- Auto Install Shadowsocks(Go) Server for CentOS/Debian/Ubuntu
- https://teddysun.com/392.html

shadowsocks-crond.sh
===============
- Check Shadowsocks(All version) Server is running or not, and start it if not running
- https://teddysun.com/525.html

shadowsocksR.sh
===============
- Auto Install ShadowsocksR Server for CentOS/Debian/Ubuntu
- https://shadowsocks.be/9.html

shadowsocks-all.sh
==================
- Auto Install Shadowsocks Server (all version) for CentOS/Debian/Ubuntu
- https://teddysun.com/486.html

haproxy.sh
===============
- Auto Install haproxy for Shadowsocks Server
- https://shadowsocks.be/10.html

Copyright (C) 2014-2019 Teddysun



本脚本适用环境
系统支持：CentOS 6+，Debian 7+，Ubuntu 12+

内存要求：≥128M

关于本脚本
脚本来至“秋水逸冰”博客

一键安装 Shadowsocks-Python， ShadowsocksR， Shadowsocks-Go， Shadowsocks-libev 版（四选一）服务端；
各版本的启动脚本及配置文件名不再重合；
每次运行可安装一种版本；
支持以多次运行来安装多个版本，且各个版本可以共存（注意端口号需设成不同）；
若已安装多个版本，则卸载时也需多次运行（每次卸载一种）；
各版本介绍
不管 Shadowsocks 有几种版本，都分为服务端和客户端，服务端是部署在服务器（VPS）上的，客户端是在你的电脑上使用的。

Shadowsocks 服务端大体上有 4 种版本，按照程序语言划分，分别为 Python ，libev ，Go ， Nodejs ，目前主流使用前 3 种。

Shadowsocks 客户端几乎包括了所有的终端设备，PC ，Mac ，Android ，iOS ，Linux 等。

默认配置
服务器端口：自己设定（如不设定，默认从 9000-19999 之间随机生成）
密码：自己设定（如不设定，默认为 teddysun.com）
加密方式：自己设定（如不设定，Python 和 libev 版默认为 aes-256-gcm，R 和 Go 版默认为 aes-256-cfb）
协议（protocol）：自己设定（如不设定，默认为 origin）（仅限 ShadowsocksR 版）
混淆（obfs）：自己设定（如不设定，默认为 plain）（仅限 ShadowsocksR 版）
备注：脚本默认创建单用户配置文件，如需配置多用户，请手动修改相应的配置文件后重启即可。

客户端下载
常规版 Windows 客户端

https://github.com/shadowsocks/shadowsocks-windows/releases

ShadowsocksR 版 Windows 客户端

https://github.com/shadowsocksrr/shadowsocksr-csharp/releases

使用方法
使用root用户登录SSH(Xftp6/Xshell6客户端免费绿色版)，运行以下命令：

wget --no-check-certificate -O shadowsocks-all.sh https://raw.githubusercontent.com/teddysun/shadowsocks_install/master/shadowsocks-all.sh
chmod +x shadowsocks-all.sh
./shadowsocks-all.sh 2>&1 | tee shadowsocks-all.log
卸载方法
若已安装多个版本，则卸载时也需多次运行（每次卸载一种）

使用root用户登录，运行以下命令：

./shadowsocks-all.sh uninstall
启动脚本
启动脚本后面的参数含义，从左至右依次为：启动，停止，重启，查看状态。

Shadowsocks-Python 版：

/etc/init.d/shadowsocks-python start | stop | restart | status

ShadowsocksR 版：

/etc/init.d/shadowsocks-r start | stop | restart | status

Shadowsocks-Go 版：

/etc/init.d/shadowsocks-go start | stop | restart | status

Shadowsocks-libev 版：

/etc/init.d/shadowsocks-libev start | stop | restart | status

各版本默认配置文件
Shadowsocks-Python 版：

/etc/shadowsocks-python/config.json

ShadowsocksR 版：

/etc/shadowsocks-r/config.json

Shadowsocks-Go 版：

/etc/shadowsocks-go/config.json

Shadowsocks-libev 版：

/etc/shadowsocks-libev/config.json

python多用户多端口配置文件示例：
配置文件路径：/etc/shadowsocks-python/config.json

{
    "server":"0.0.0.0",
    "local_address":"127.0.0.1",
    "local_port":1080,
    "port_password":{
         "8989":"password0",
         "9001":"password1",
         "9002":"password2",
         "9003":"password3",
         "9004":"password4"
    },
    "timeout":300,
    "method":"your_encryption_method",
    "fast_open": false
}
ShadowsocksR多用户多端口配置文件示例：
配置文件路径：/etc/shadowsocks-r/config.json

{
"server":"0.0.0.0",
"server_ipv6": "[::]",
"local_address":"127.0.0.1",
"local_port":1080,
"port_password":{
    "8989":"password1",
    "8990":"password2",
    "8991":"password3"
},
"timeout":300,
"method":"aes-256-cfb",
"protocol": "origin",
"protocol_param": "",
"obfs": "plain",
"obfs_param": "",
"redirect": "",
"dns_ipv6": false,
"fast_open": false,
"workers": 1
}
Go多用户多端口配置文件示例：
配置文件路径：/etc/shadowsocks-go/config.json

{
    "port_password":{
         "8989":"password0",
         "9001":"password1",
         "9002":"password2",
         "9003":"password3",
         "9004":"password4"
    },
    "method":"your_encryption_method",
    "timeout":600
}
分享到：    
未经允许不得转载：
作者:晓鹄， 转载或复制请以 超链接形式 并注明出处 晓鹄博客。
原文地址：《最新SSR一键安装脚本》 发布于2019-04-11
