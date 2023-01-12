---
title: Kali配置及指令
category: 笔记
tags:
  - linux
  - 配置
banner_img: /img/banner/kali.jpg
index_img: /img/cover/kali.jpg
excerpt: kali中配置各种初始化信息及常用命令
date: 2023-01-06 21:31:53
---
kali是deb架构的机器
## 配置clash
1.下载clashForWindowsLinux.tar.gz（已放入奶牛快传我的文件中）

2.解压
```bash
$ tar -zxvf clashForWindowsLinux.tar.gz
```

3.进入解压后的文件
```bash
$ cd clashForWindowsLinux
```

4.启动clash
```bash
$ ./cfw
```

5.在Clash中导入clash订阅

6.在firefox中点击设置，选择General
![](/img/content/linux_clash/general.jpg)

7.划到最底下，点击network Settings
![](/img/content/linux_clash/net_settings.jpg)

8.配置网关信息如下
![](/img/content/linux_clash/kali_gateway.jpg)

## 在ubuntu、mint中配置clash
1.下载clashForWindowsLinux.tar.gz（已放入奶牛快传我的文件中）

2.解压
```bash
$ tar -zxvf clashForWindowsLinux.tar.gz
```

3.进入解压后的文件
```bash
$ cd clashForWindowsLinux
```

4.启动clash
```bash
$ ./cfw
```

5.在Clash中导入clash订阅

6.配置linux网关代理如下
![](/img/content/linux_clash/gateway.jpg)

## 配置中文输入法
安装输入法框架
```bash
$ apt install fcitx fcitx-googlepinyin
```
安装完后重启reboot
打开Fcitx 配置，点击左下角的+号，取消勾选`Onlu show current language`
选择Google Pinyin并添加
将Google Pinyin上移到第一行
按Ctrl+空格切换输入法

## 常用命令
```bash
# 使用root权限
$ sudo su

# 安装deb文件
$ dpkg -i 文件名.deb

# 文件路径有空格时的cd，有空格的文件名用双引号圈起
$ cd /xxx/xxx/"有空格的文件名"

# 重启
$ reboot

# 解压.tar文件
tar -xvf 文件名.tar

# 解压.tar.gz文件
tar -zxvf 文件名.tar
```