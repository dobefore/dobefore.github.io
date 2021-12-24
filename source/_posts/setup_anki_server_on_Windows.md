---
title: 搭建Anki局域网同步服务器(Windows)
date: 2020-05-30 12:08:17
readmore: true
categories: tools
tags:
- Anki
- 搭建Anki服务器
- Windows
---

这个教程是介绍搭建anki服务器的**Windows免安装**软件（64位哦），文章末尾标准版**百度云盘链接自取**哟；如果需要远程安装，需要收取**￥3**至**5**元的服务费哟（可以在咸鱼上更快联系到我哟）。

**配置满足的条件**有：

- Windows Anki版本2.1（版本：帮助-->关于）
- 安卓平台 Ankidroid 版本 >=2.8
- 同步时局域网（手机热点，WIFI）内和在电脑旁
- IOS anki （ipad，iphone等）不能同步。

**首先运行**引导配置程序，请双击**deployer.exe。**

## Attention:请先打开手机Anki查看版本（设置-->高级设置-->关于）

为什么要区分2.10和2.10以后呢？前往下面的问答区 Q2。
## 一、检查Anki版本

安装上面所说的版本。

点击下一步。。。

[![Rdjixe.jpg](https://z3.ax1x.com/2021/06/29/Rdjixe.jpg)](https://imgtu.com/i/Rdjixe)
## 二、更改电脑Anki IP同步地址

在这里，你需要选择手机Anki版本的范围，是<2.10?比如2.9.7，2.8；还是>=2.10?比如2.10，2.10.5，2.14。选择后，点击提交选择，等待点击下一步。

### [![RdjArd.jpg](https://z3.ax1x.com/2021/06/29/RdjArd.jpg)](https://imgtu.com/i/RdjArd)

1.手机开启在定义同步服务器，进入 设置->高级设置->自定义同步服务器（点击后勾选）

2.填写引导程序界面的同步地址和媒体文件同步地址（默认anki版本范围<2.10），点击下一步。。。

[![RdvKT1.jpg](https://z3.ax1x.com/2021/06/29/RdvKT1.jpg)](https://imgtu.com/i/RdvKT1)

## 三、将服务器端启动程序发送到桌面快捷方式

这里会有弹框提示即将打开文件夹，确认后，在打开的文件夹找到 makelnk.vbs ,双击它。

[![RdXrUP.png](https://z3.ax1x.com/2021/06/29/RdXrUP.png)](https://imgtu.com/i/RdXrUP)



[![RdXDEt.png](https://z3.ax1x.com/2021/06/29/RdXDEt.png)](https://imgtu.com/i/RdXDEt)



然后就在桌面看到了上面的图标，点击下一步。。。

## 四、新建账号/账号管理

选择 添加账号 ，再点击 提交选择，会出现输入框，输入简单的用户名和密码 ，点击 提交输入，即添加成功，点击下一步。。。

[![RdXs4f.png](https://z3.ax1x.com/2021/06/29/RdXs4f.png)](https://imgtu.com/i/RdXs4f)

## 五、打开同步服务、Anki切换配置方案,填写账号

1.在桌面找到第五步发送的快捷方式Anki_server，双击后会出现黑色窗口（同步过程中保持运行），可最小化运行。如果采用DHCP动态分配IP的设备（比如校园网），请下翻至问答区Q3.

[![RdX0HI.png](https://z3.ax1x.com/2021/06/29/RdX0HI.png)](https://imgtu.com/i/RdX0HI)



2.打开电脑 Anki，建议 到**文件-->切换配置方案-->添加**新的配置方案并进入（如果有牌组，先导出），点击同步，输入刚刚创建的账号密码，成功后再导入牌组。



**百度网盘链接:**

**Windows Anki** ：[Anki官网下载](https%3A//apps.ankiweb.net/)，[PC 历史版本](https%3A//github.com/ankitects/anki/releases)

**Ankidroid**：[百度网盘链接（提取码：2020）](https%3A//pan.baidu.com/s/1_sEx8PXrraQuXlsfx_Y3EA)，[F-droid市场下载](https%3A//f-droid.org/packages/com.ichi2.anki/)，[gtihub下载](https%3A//github.com/ankidroid/Anki-Android/releases)

**服务器端软件**（提取码：2021）：[点这里](https://pan.baidu.com/s/1x6K2Q27lVvyiBDNIQpQl2w)



**阿里云盘链接：**

**服务器端软件**[点这里](https://www.aliyundrive.com/s/nRavoNX7r26)



**问答区：**

**Q1：配置并打开服务器后，电脑端anki能够同步，手机端却不行？**

A：1.手机端anki IP是否配置正确，比如https去掉s 2.手机和电脑是否在同一局域网下 3.电脑开启了防火墙，把防火墙关掉。

**Q2：为什么会有<2.10和>=2.10的手机Anki版本的区分？**

其实是Ankidroid9及以后Anki不被允许http传输文件，也就是说你的手机安卓版本在9以内，不管Anki版本是2.8还是2.14都可以选择<2.10的配置。

**Q3:某天打开服务端软件开始同步，发现突然出现错误，明明账号和密码都对，以前都可以同步？**

可能设备采用DHCP动态分配IP,说明服务端所在的电脑被分配的IP已经发生变动；每次服务端软件anki_server(ankisyncd)启动会检测本机ip是否发生变化，如果发生变动，会自动修改电脑Anki的IP，并将详细的新地址打印到服务端黑色窗口，需要你手动填写到安卓Ankidroid的相应界面。
[![TNF8h9.jpg](https://s4.ax1x.com/2021/12/24/TNF8h9.jpg)](https://imgtu.com/i/TNF8h9)



**参考：**

[ankicommunity/anki-sync-server-rs](https://github.com/ankicommunity/anki-sync-server-rs)

