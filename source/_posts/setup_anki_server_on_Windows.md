---
title: 搭建Anki局域网同步服务器(Windows)
date: 2020-05-30 12:08:17
categories: tools
tags:
- Anki
- 搭建Anki服务器
- Windows
---

这个教程是介绍搭建anki服务器的**Windows免安装**软件（64位哦），文章末尾标准版**百度云盘链接自取**哟；其优点是简单易用，点击击软件即可开启服务器，并且第一次配置也是非常easy！如果需要远程安装，需要收取**￥3**至**5**元的服务费哟（可以在咸鱼上更快联系到我哟）。



**配置满足的条件**有（Anki各版本软件可在文末下载）：

- Windows Anki版本2.1**（已支持**2.1.36及以后**、**2.1.26及以前**版本：帮助-->关于）
- python3.8（不用自己下载安装，**2.1.36及以后**不需要安装python和依赖）
- 安卓平台 Ankidroid 版本 **2.13**及**以前**版本（注：2.10及以后版本请阅读这个教程[Ankidoid 2.10搭建局域网服务器](https://sampuly.gitee.io/Windows%E6%90%AD%E5%BB%BA%E5%9F%BA%E4%BA%8Ehttps%E5%8D%8F%E8%AE%AE%E7%9A%84Anki%E5%B1%80%E5%9F%9F%E7%BD%91%E5%90%8C%E6%AD%A5%E6%9C%8D%E5%8A%A1%E5%99%A8.html)
- 同步时局域网（手机热点，WIFI）内和在电脑旁
- IOS anki （ipad，iphone等）不能同步。



**首先运行**第一次引导配置程序，双击**deploy_helper.exe**开始引导配置，对于Win7以及打开auto_install闪退的用户，请双击**deploy_helper.exe。**

**Attention:请先打开手机Anki查看版本（设置-->高级设置-->关于），如果<2.10,阅读本教程;如果>=2.10,请移步至[Ankidoid 2.10搭建局域网服务器](https://sampuly.gitee.io/Windows%E6%90%AD%E5%BB%BA%E5%9F%BA%E4%BA%8Ehttps%E5%8D%8F%E8%AE%AE%E7%9A%84Anki%E5%B1%80%E5%9F%9F%E7%BD%91%E5%90%8C%E6%AD%A5%E6%9C%8D%E5%8A%A1%E5%99%A8.html) (如网页打不开，请看文件夹内的离线教程)**

## 一、python及其依赖的安装

## 1.python安装（要求版本 3.8）

PC Anki 版本**2.1.36及以后 ** 不需要安装python。

不用自己下载，文件夹提供有安装包，安装时记得勾选添加python路径到环境变量，如下图。
![Add Python To PATH](https://s1.ax1x.com/2020/06/15/NpzuJf.jpg)

## 2.python依赖的安装
按照引导程序，输入数字，进行下一步操作。
## 二、电脑版anki的和手机版anki IP设置
## 1.电脑版anki IP设置
根据对应的电脑Anki版本输入相应数字，自动复制插件和更新电脑 Anki IP，然后重启Anki。

## 2.安卓手机版anki IP配置

配合引导程序和文件夹，进入目录–>电脑端和手机端anki的配置 ,如有疑问，欢迎私聊。

## 三、新建账号及打开同步服务

## 1.将服务器软件发送到桌面快捷方式

按照引导程序来操作

## 2.新建账号

打开服务器软件，点击**添加账号**



[![添加用户](https://s1.ax1x.com/2020/05/25/tpIvO1.md.jpg)](https://imgchr.com/i/tpIvO1)



## 3.打开同步服务

点击**打开服务器**，出现如下界面即表示正常,同步时请保持**黑色窗口打开**（可最小化）。打开电脑 Anki，建议 **到文件-->切换配置方案-->添加**新的配置方案并进入，点击同步，输入刚刚创建的账号密码。

[![打开服务器](https://s1.ax1x.com/2020/05/25/tpIjyR.md.jpg)](https://imgchr.com/i/tpIjyR)

接着就可以享受畅快的同步之旅啦。

**百度网盘链接:**

**Windows Anki ：**[Anki中国下载地址](http%3A//www.ankichina.net/resource/winAnki)，[Anki官网下载](https%3A//apps.ankiweb.net/)，[PC 历史版本](https%3A//github.com/ankitects/anki/releases)

**Ankidroid**：[百度网盘链接（提取码：2020）](https%3A//pan.baidu.com/s/1_sEx8PXrraQuXlsfx_Y3EA)，[F-droid市场下载](https%3A//f-droid.org/packages/com.ichi2.anki/)，[gtihub下载](https%3A//github.com/ankidroid/Anki-Android/releases)

**服务器端软件（2.1.26及以前版本）**压缩包（提取码：2021）： [点这里](https://pan.baidu.com/s/1Xrn-d2j0swujkcOCVh5dxg)

**服务器端软件（2.1.36及以后）**压缩包（提取码：2021）：[点这里](https://pan.baidu.com/s/10V29Hk6XJNWsd-nPHxa7fA)



链接不可用欢迎留言反馈哟！

**无法正常配置和使用问题自检：**

**Q1：点击打开服务器，命令行窗口闪退？**

A：1.python依赖库是否安装到位 2.python是否能在CMD中启动 3.双击能否打开py文件（是否将python设置为默认打开方式）

**Q2：配置并打开服务器后，电脑端anki能够同步，手机端却不行？**

A：1.手机端anki IP是否配置正确，比如https去掉s 2.手机和电脑是否在同一局域网下 3.电脑开启了防火墙，把防火墙关掉。

**Q3：对于2.1.36及以后版本服务器软件开启后，不能下载插件？**

A：1.关闭服务器软件黑色窗口 2.双击 **kill_****nginx.exe (**和auto_install 在一个 目录) 3.待插件下载后，再打开服务器软件



**参考：**

[CentOS7自建Anki同步服务器(python3)](https://www.xiebruce.top/881.html)

[tsudoko/anki-sync-server](https%3A//github.com/tsudoko/anki-sync-server.git)

[ankicommunity](https://github.com/ankicommunity/anki-sync-server)

