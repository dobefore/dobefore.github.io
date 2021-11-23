---
title: Windows搭建基于https协议的Anki局域网同步服务器
date: 2020-06-10 11:53:41
readmore: true
categories: tools
tags:
- Anki
- 搭建Anki服务器
---

> 这篇是配合Ankidroid版本>= ` 2.10` 使用的，若不符合情况的请阅读教程[Anki自建局域网同步服务器](https://dobefore.github.io/setup_anki_server_on_Windows/)

---

**配置满足的条件**有：

- Windows Anki版本2.1**（**已支持**2.1.44**及以前、2.1.26及以前版本：帮助-->关于）
- 安卓平台 Ankidroid 版本 **2.14**及**以前**版本
- 同步时局域网（手机热点，WIFI）内和在电脑旁
- IOS anki （ipad，iphone等）不能同步。

**首先运行**引导配置程序，请双击**deploy_helper.exe。**

## Attention:请先打开手机Anki查看版本（设置-->高级设置-->关于）

为什么要区分2.10和2.10以后呢？前往下面的问答区 Q3。

## 一、检查英文路径及Anki版本

确保下载的文件夹放置在全英文路径下，为什么？nginx似乎在英文路径下才能运行。

及安装上面所说的版本。

点击下一步。。。

[![Rdjixe.jpg](https://z3.ax1x.com/2021/06/29/Rdjixe.jpg)](https://imgtu.com/i/Rdjixe)

## 二、检查电脑Anki版本是否需要安装Python

Anki版本在**2.1.36-2.1.40**因为成功打包成exe，所以不需要安装Python，其他的版本需要安装Python;不复杂的，一点两点三点~，如果你已经安装了python3，那么不用重新安装了，程序会自行安装需要的模块。

如何安装Python呢？文件夹内提供python3.9,程序会弹出确认安装python的弹框，确认后，进入python安装界面。

[![RdjP2D.jpg](https://z3.ax1x.com/2021/06/29/RdjP2D.jpg)](https://imgtu.com/i/RdjP2D)



在Python安装界面中，先点击复选框 Add Python 3.9 to PATH,然后点击Install Now. 静静地等待安装完成。



![Add Python To PATH](https://s1.ax1x.com/2020/06/15/NpzuJf.jpg)

关闭我们的引导程序并重新打开，点击下一步。这时候会出现一个进度条，这是表示python模块复制的进度，满了，点击下一步。

## 三、更改电脑Anki IP同步地址

在这里，你需要选择手机Anki版本的范围，是<2.10?比如2.9.7，2.8；还是>=2.10?比如2.10，2.10.5，2.14。选择后，点击提交选择，等待点击下一步。

### [![Rdv1fK.png](https://z3.ax1x.com/2021/06/29/Rdv1fK.png)](https://imgtu.com/i/Rdv1fK)

## 四、配置手机Anki IP同步地址

1.在桌面找到`rootCA.crt` ,双击它，会弹出证书导入界面，按照图片操作。

[![tovFJS.jpg](https://s1.ax1x.com/2020/06/10/tovFJS.jpg)](https://imgtu.com/i/tovFJS)

并将上述文件复制到手机（QQ、USB、微信），并在手机中找到它，触摸弹出证书安装界面。

[![RwSESf.jpg](https://z3.ax1x.com/2021/06/29/RwSESf.jpg)](https://imgtu.com/i/RwSESf)



操作后，点击引导程序上方右侧 确认，随即出现io地址。

2.手机开启在定义同步服务器，进入 设置->高级设置->自定义同步服务器（点击后勾选）

2.填写引导程序界面的同步地址和媒体文件同步地址（默认anki版本范围>=2.10），点击下一步。。。

[![RdvlY6.png](https://z3.ax1x.com/2021/06/29/RdvlY6.png)](https://imgtu.com/i/RdvlY6)



## 五、将服务器端启动程序发送到桌面快捷方式

这里会有弹框提示即将打开文件夹，确认后，在打开的文件夹找到 makelnk.vbs ,双击它。

[![RdXrUP.png](https://z3.ax1x.com/2021/06/29/RdXrUP.png)](https://imgtu.com/i/RdXrUP)



[![RdXDEt.png](https://z3.ax1x.com/2021/06/29/RdXDEt.png)](https://imgtu.com/i/RdXDEt)



然后就在桌面看到了上面的图标，点击下一步。。。

## 六、新建账号/账号管理

选择 添加账号 ，再点击 提交选择，会出现输入框，输入简单的用户名和密码 ，点击 提交输入，即添加成功，点击下一步。。。

[![RwpAE9.png](https://z3.ax1x.com/2021/06/29/RwpAE9.png)](https://imgtu.com/i/RwpAE9)



## 七、打开同步服务、Anki切换配置方案,填写账号

1.在桌面找到第五步发送的快捷方式Anki_server，双击后会出现黑色窗口（同步过程中保持运行），可最小化运行。

[![RdX0HI.png](https://z3.ax1x.com/2021/06/29/RdX0HI.png)](https://imgtu.com/i/RdX0HI)



2.打开电脑 Anki，建议 到**文件-->切换配置方案-->添加**新的配置方案并进入（如果有牌组，先导出），点击同步，输入刚刚创建的账号密码，成功后再导入牌组。



**百度网盘链接:**

**Windows Anki ：**[Anki中国下载地址](http%3A//www.ankichina.net/resource/winAnki)，[Anki官网下载](https%3A//apps.ankiweb.net/)，[PC 历史版本](https%3A//github.com/ankitects/anki/releases)

**Ankidroid**：[百度网盘链接（提取码：2020）](https%3A//pan.baidu.com/s/1_sEx8PXrraQuXlsfx_Y3EA)，[F-droid市场下载](https%3A//f-droid.org/packages/com.ichi2.anki/)，[gtihub下载](https%3A//github.com/ankidroid/Anki-Android/releases)

**服务器端软件（2.1.26及以前版本）**压缩包（提取码：2021）： [点这里](https://pan.baidu.com/s/1Xrn-d2j0swujkcOCVh5dxg)
**服务器端软件（2.1.36-2.1.40）**压缩包（提取码：2021）：[点这里](https://pan.baidu.com/s/15EPOdg2TiuQB-My8e7h7SA)
**服务器端软件（2.1.41及以后）**压缩包（提取码：2021）：[点这里](https://pan.baidu.com/s/1d1UxhiZ3scONmZ4ilqk5Kg)



**问答区：**

**Q1：配置并打开服务器后，电脑端anki能够同步，手机端却不行？**

A：1.手机端anki IP是否配置正确，比如https去掉s 2.手机和电脑是否在同一局域网下 3.电脑开启了防火墙，把防火墙关掉。

**Q2:2.1.36版本及以后，打开服务器软件后，不能正常下载插件？**

A：1.关闭服务器软件黑色窗口 2.双击 **kill_*****nginx.exe (**和auto*_install 在一个 目录) 3.待插件下载后，再打开服务器软件

**Q3：为什么会有<2.10和>=2.10的手机Anki版本的区分？**

其实是Ankidroid9及以后Anki不被允许http传输文件，也就是说你的手机安卓版本在9以内，不管Anki版本是2.8还是2.14都可以选择<2.10的配置。

**Q4：2.1.41版本以后，出现强制完全同步？**

按照下面图示操作后，点击同步。

[![RwpwDg.jpg](https://z3.ax1x.com/2021/06/29/RwpwDg.jpg)](https://imgtu.com/i/RwpwDg)



[![RwpdKS.jpg](https://z3.ax1x.com/2021/06/29/RwpdKS.jpg)](https://imgtu.com/i/RwpdKS)

---





**参考文章：**

[CentOS7自建Anki同步服务器(python3)](https://www.xiebruce.top/881.html)

[本地https快速解决方案——mkcert](https://blog.dteam.top/posts/2019-04/本地https快速解决方案mkcert.html)

[tsudoko/anki-sync-server](https%3A//github.com/tsudoko/anki-sync-server.git)

[ankicommunity](https://github.com/ankicommunity/anki-sync-server)

