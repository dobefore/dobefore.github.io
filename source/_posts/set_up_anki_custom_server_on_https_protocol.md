---
title: Windows搭建基于https协议的Anki局域网同步服务器
date: 2020-06-10 11:53:41
readmore: true
categories: tools
tags:
- Anki
- 搭建Anki服务器
---

---

**配置满足的条件**有：

- Windows Anki版本2.1（版本：帮助-->关于）
- 安卓平台 Ankidroid 版本 >=2.8
- 同步时局域网（手机热点，WIFI）内和在电脑旁
- IOS anki （ipad，iphone等）不能同步。

**首先运行**引导配置程序，请双击**deployer.exe。**

## 一、检查Anki版本

安装上面所说的版本。

点击下一步。。。

[![bTGMlD.png](https://s1.ax1x.com/2022/03/12/bTGMlD.png)](https://imgtu.com/i/bTGMlD)



## 二、设置Anki同步地址

#### （1）添加根证书到受信任的系统证书区

有如下弹窗请点击是。

### 

#### （2）设置手机Anki同步地址

1.在桌面找到`rootCA.crt` ，用QQ、USB、微信等发送文件到手机，并在手机中找到它，触摸弹出证书安装界面。进安装一次，后续部署过程中无需此操作。

[![bTGKSO.png](https://s1.ax1x.com/2022/03/12/bTGKSO.png)](https://imgtu.com/i/bTGKSO)



2.手机开启在定义同步服务器，进入 设置->高级设置->自定义同步服务器（点击后勾选）

2.填写引导程序界面的同步地址和媒体文件同步地址，点击开关进入下一步。。。

[![bT8voq.png](https://s1.ax1x.com/2022/03/12/bT8voq.png)](https://imgtu.com/i/bT8voq)



## 三、将服务器端启动程序发送到桌面快捷方式，并添加到开始菜单

[![bTGeFx.png](https://s1.ax1x.com/2022/03/12/bTGeFx.png)](https://imgtu.com/i/bTGeFx)



添加到开始菜单意味着可以通过开始搜索框快捷启动软件

然后就在桌面看到了上面的图标，点击下一步。。。

## 四、新建账号/账号管理

选择 添加账号 ，再点击 提交选择，会出现输入框，输入简单的用户名和密码 ，点击 提交，即添加成功，点击下一步。。。



[![bT8jwn.png](https://s1.ax1x.com/2022/03/12/bT8jwn.png)](https://imgtu.com/i/bT8jwn)

## 五、打开同步服务、Anki切换配置方案,填写账号

1.在桌面找到第五步发送的快捷方式Anki_server，双击后会出现黑色窗口（同步过程中保持运行），可最小化运行。如果采用DHCP动态分配IP的设备（比如校园网），请下翻至问答区Q2.

[![bTGmY6.png](https://s1.ax1x.com/2022/03/12/bTGmY6.png)](https://imgtu.com/i/bTGmY6)

2.打开电脑 Anki，建议 到**文件-->切换配置方案-->添加**新的配置方案并进入（如果有牌组，先导出），点击同步，输入刚刚创建的账号密码，成功后再导入牌组。



**百度网盘链接:**

**Windows Anki **，[Anki官网下载](https%3A//apps.ankiweb.net/)，[PC 历史版本](https%3A//github.com/ankitects/anki/releases)

**Ankidroid**：[百度网盘链接（提取码：2020）](https%3A//pan.baidu.com/s/1_sEx8PXrraQuXlsfx_Y3EA)，[F-droid市场下载](https%3A//f-droid.org/packages/com.ichi2.anki/)，[gtihub下载](https%3A//github.com/ankidroid/Anki-Android/releases)

**服务器端软件**（提取码：2021）：[点这里](https://pan.baidu.com/s/1NMGVGzJ2nm6wmWSZDNn5iQ)



**阿里云盘链接：**

**服务器端软件**[点这里](https://www.aliyundrive.com/s/inbib8Fkx21)

**问答区：**

**Q1：配置并打开服务器后，电脑端anki能够同步，手机端却不行？**

A：1.手机端anki IP是否配置正确，比如https去掉s 2.手机和电脑是否在同一局域网下 3.电脑开启了防火墙，把防火墙关掉。

**Q2:某天打开服务端软件开始同步，发现突然出现错误，明明账号和密码都对，以前都可以同步？**

可能设备采用DHCP动态分配IP,说明服务端所在的电脑被分配的IP已经发生变动；每次服务端软件anki_server(ankisyncd)启动会检测本机ip是否发生变化，如果发生变动，会自动修改电脑Anki的IP，并将详细的新地址打印到服务端黑色窗口，需要你手动填写到安卓Ankidroid的相应界面。
[![bTGnfK.png](https://s1.ax1x.com/2022/03/12/bTGnfK.png)](https://imgtu.com/i/bTGnfK)



**参考文章：**

[本地https快速解决方案——mkcert](https://blog.dteam.top/posts/2019-04/本地https快速解决方案mkcert.html)

[ankicommunity/anki-sync-server-rs](https://github.com/ankicommunity/anki-sync-server-rs)

