---
title: linux下安装和配置Clash
category: 笔记
tags:
  - linux
  - 科学上网
banner_img: /img/banner/linux_clash.jpg
index_img: /img/cover/linux_clash.jpg
excerpt: 在linux中配置clash科学上网
date: 2023-01-06 21:31:53
---
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

## 在kali中配置
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