---
title: Windows搭建基于https协议的Anki局域网同步服务器
date: 2020-06-10 11:53:41
categories: tools
tags:
- Anki
- 搭建Anki服务器
---

> 这篇是配合Ankidroid版本>= ` 2.10` 使用的，若不符合情况的请阅读教程[Anki自建局域网同步服务器](https://sampuly.gitee.io/%E6%90%AD%E5%BB%BA-Anki%E5%B1%80%E5%9F%9F%E7%BD%91%E5%90%8C%E6%AD%A5%E6%9C%8D%E5%8A%A1%E5%99%A8.html)

---

**Tips**：为什么总有小伙伴分不出大小，举两个例子：` 2.9.7` <` 2.10`，` 2.11` > `2.10`。

**配置满足的条件**有（Anki各版本软件可在文末下载）：

- Windows Anki版本2.1（已支持**2.1.36**及以后、**2.1.26及以前**版本：帮助-->关于）
- python3.8（不用自己下载，**2.1.36及以后**不需要安装python和依赖）
- 安卓平台 Ankidroid  2.10及以后版本
- 同步时局域网（手机热点，WIFI）内和在电脑旁
- IOS anki （ipad，iphone等）不能同步。

**首先运行**第一次引导配置程序，双击**deploy_helper.exe**开始引导配置，对于Win7以及打开auto_install闪退的用户，请双击**deploy_helper.exe。**

# 一、python及其依赖的安装

## 1.python安装（要求版本 3.8）

PC Anki 版本**2.1.36及以后** 不需要安装python。

不用自己下载，文件夹提供有安装包，安装时记得勾选添加python路径到环境变量，如下图。
![Add Python To PATH](https://s1.ax1x.com/2020/06/15/NpzuJf.jpg)

## 2.python依赖的安装

按照引导程序，输入数字，进行下一步操作。

# 二、电脑版anki的和手机版anki IP设置

## 1.电脑版anki IP设置

根据对应的电脑Anki版本输入相应数字，自动复制插件和更新电脑 Anki IP，然后重启Anki。

## 2.电脑安装证书、手机安装证书

插件安装后，根据引导程序输入数字2进入添加Anki环境变量操作。

### (1)添加Anki环境变量

**win10** 亲测自动添加Anki环境变量，**Win7**如果发现不能成功，请按照下述步骤手动添加。

~~打开搜索框 ，输入框里输入`env` ,单击 `编辑账户的环境变量` ,单击用户变量下的 `新建`。~~

~~变量名输入：ANKI_NOVERIFYSSL~~

~~值：1~~

~~如下图~~

![添加Anki环境变量](https://s1.ax1x.com/2020/06/10/tocny9.jpg)

点击确认，再点击右下角的确认

### (2)生成并安装电脑证书

回到**auto_install** ,根据提示输入数字生成并安装**Local CA**。

**PC导入rootCA.crt证书**

在桌面找到**rootCA.crt**，双击启动导入程序，将证书导入`受信任的根证书颁发机构`。

![导入证书](https://s1.ax1x.com/2020/06/10/tovFJS.jpg)

再将**rootCA.crt**用QQ或USB复制到手机任意位置（确保到时候能找到）

### (3)手机CA证书安装

使用手机QQ/TIM或者文件浏览器找到文件`rootCA.crt`，触摸打开，如果提示以`证书安装程序`打开，请确认；证书名称随意填。

如果提示 `无法安装证书,因为无法读取证书文件`，~~进入手机`设置-->安全（安全和隐私,往下翻）-->从SD卡安装（证书）-->找到文件（rootCA.crt）并点击`,证书名称随意填.~~

## 3.手机Anki IP设置

按照**auto_install**提示进行填写

# 三、新建账号及打开同步服务

## 1.将服务器软件发送到桌面快捷方式

按照引导程序来操作

## 2.新建账号

打开服务器软件，点击**添加账号**

[![添加账号](https://s1.ax1x.com/2020/05/25/tpIvO1.jpg)](https://imgchr.com/i/tpIvO1)

## 3.打开同步服务

点击**打开服务器**，出现如下界面即表示正常，同步时请保持**黑色窗口打开**（可最小化）。打开电脑 Anki，建议 **到文件–>切换配置方案–>添加**新的配置方案并进入，点击同步，输入刚刚创建的账号密码。

[![打开服务器](https://s1.ax1x.com/2020/05/25/tpIjyR.md.jpg)](https://imgchr.com/i/tpIjyR)

接着就可以享受畅快的同步之旅啦。

**百度网盘链接**

**Windows Anki ：**[Anki中国下载地址](http%3A//www.ankichina.net/resource/winAnki)，[Anki官网下载](https%3A//apps.ankiweb.net/)，[PC 历史版本](https%3A//github.com/ankitects/anki/releases)

**Ankidroid**：[百度网盘链接（提取码：2020）](https%3A//pan.baidu.com/s/1_sEx8PXrraQuXlsfx_Y3EA)，[F-droid市场下载](https%3A//f-droid.org/packages/com.ichi2.anki/)，[gtihub下载](https%3A//github.com/ankidroid/Anki-Android/releases)

**服务器端软件（2.1.26及以前版本）**压缩包（提取码：2021）： [点这里](https://pan.baidu.com/s/1Xrn-d2j0swujkcOCVh5dxg)

**服务器端软件（2.1.36及以后）**压缩包（提取码：2021）：[点这里](https://pan.baidu.com/s/10V29Hk6XJNWsd-nPHxa7fA)



链接不可用欢迎留言反馈哟

---



**无法正常配置和使用问题自检：**

**Q1：点击打开服务器，命令行窗口闪退？**

**A：**1.python依赖库是否安装到位 2.python是否能在CMD中启动 3.双击能否打开py文件（是否将python设置为默认打开方式）

**Q2：配置并打开服务器后，电脑端anki能够同步，手机端却不行？**

**A：**1.手机端anki IP是否配置正确 2.手机和电脑是否在同一局域网下 3.电脑开启了防火墙，把防火墙关掉。

**Q3：对于2.1.36及以后版本服务器软件开启后，不能下载插件？**

A：1.关闭服务器软件黑色窗口 2.双击 **kill_****nginx.exe (**和auto_install 在一个 目录) 3.待插件下载后，再打开服务器软件

**参考文章：**

[CentOS7自建Anki同步服务器(python3)](https://www.xiebruce.top/881.html)

[本地https快速解决方案——mkcert](https://blog.dteam.top/posts/2019-04/本地https快速解决方案mkcert.html)

[tsudoko/anki-sync-server](https%3A//github.com/tsudoko/anki-sync-server.git)

[ankicommunity](https://github.com/ankicommunity/anki-sync-server)

