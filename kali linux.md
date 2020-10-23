---

title: kali linux

categories: kali

toc: true

mathjax: true

tags: 

- kali

- 工具

- 逆向

widgets:

-

    type: toc

    position: left

-

    type: profile

    position: left

    author: Runope

    # Author title

    author_title: 不知不论，不做不论

    # Author's current location

    location: Nanjin，jiangsu

    # URL or path to the avatar image

    avatar: https://en.gravatar.com/userimage/194935117/7129e2095de79a9dd97e5cc344acaba2?size=200

    # Whether show the rounded avatar image

    avatar_rounded: false

    # Email address for the Gravatar

    gravatar: 275358499@qq.com

    # URL or path for the follow button

    follow_link: 'https://github.com/runope'

-

    type: recent_posts

    position: left

---



# Root问题



最好的解决思路：直接使用Root账户，但是途中还是有很多配置，下面具体讲这些步骤：



1. 使用kali账户进入系统，修改root密码sudo passwd root

2. 用root账户进入系统

3. 解决terminal配色问题：cp  /home/{your user name}/.bashrc     /root/.bashrc

4. 解决有些程序所属组问题， chown -R root:root /home/                      chgrp -R root:root /home/


<!--more-->

# kali系统源



```bash

mousepad /etc/apt/sources.list

# add zju source

deb http://mirrors.zju.edu.cn/kali kali-rolling main contrib non-free

deb-src http://mirrors.zju.edu.cn/kali kali-rolling main contrib non-free





apt-get update &apt-get upgrade

apt-get dist-upgrade

#删除以下载的包

apt-get clean

```



# pip源



```bash

# 如果要安装pip

apt install python3-pip

# 设置豆瓣源

pip config set global.index-url https://pypi.douban.com/simple/

```



# Terminal无法调整字体大小问题



```txt

修改配置文件，用户家目录下

~/.config/qterminal.org/qterminal.ini

下面两行，第一行是字体，第二行是大小



fontFamily=Fira Code

fontSize=10



修改的时候要先把终端关闭了,直接用文件夹查看，View-》Show Hidden Files

```







# 安装小工具



> 两个文件比较工具：apt install kompare

> 16进制查看工具：apt install bless

> 16进制查看工具：自带的hexdump：  hexdump -C -n 10 {filename} 

> 				-n10指查看前10字节

> 编辑十六进制： apt install hexedit

> Radare2

> Radare2教程：https://github.com/Maijin/radare2-workshop-2015







# 安装Ghidra







其实，卡里内部已经有多个版本的jre，在目录/usr/lib/jvm/中，ghidra需要jdk11，我们只需要执行apt install default-jdk就能安装jdk11，之后./ghidraRun，输入路径/usr/lib/jvm/java-11-openjdk-amd64/即可
