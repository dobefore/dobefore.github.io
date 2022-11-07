---
title: set_up_anki_custom_server_new
readmore: true
date: 2022-08-31 11:00:57
tags: 
- Anki
- 搭建Anki服务器
- windows
---
## 前言
在文章[set_up_anki_custom_server_on_https_protocol](https://dobefore.github.io/set_up_anki_custom_server_on_https_protocol/)里面提供了Ankidroid几乎全版本（>2.8）的支持，但是由于部署软件兼容性并不能正常滴在所有Windows机型上运行。所以这篇文章介绍更广兼容性的方法，需要安装我们文件夹中提供的Ankidroid版本（当然也可以等待2.16正式版的发布），关于为什么会有版本要求看这里[ankidroid版本要求原因与版本选择](#ankidroid版本要求原因与版本选择)。

接下来是一份相当简单的引导教程，可以找个合适的位置存放下载好的文件夹用来**存放同步数据**。

## 第一步  打开配置文件ankisyncd.toml，设置你的同步账号和密码
如果跳过这一步的话，会得到账号username:`test`,password:`123456`。如下图，账号可以随意填写，输入后记得保存。
[![v4GRLq.png](https://s1.ax1x.com/2022/08/31/v4GRLq.png)](https://imgse.com/i/v4GRLq)

## 第二步 双击启动ankiserver，查看同步地址（用于Ankidroid的配置）
[![xvcWQO.png](https://s1.ax1x.com/2022/11/07/xvcWQO.png)](https://imgse.com/i/xvcWQO)

## 第三步 打开Anki，输入账号(来自第一步)，点击同步
保持第二步服务端处于开启状态（黑屏打开状态），到**工具（tools）-->首选项(preferences)-->网络（network）-->退出账号(logout)**,然后退出Anki再打开，输入第一步的账号。
[![v4gcLV.png](https://s1.ax1x.com/2022/08/31/v4gcLV.png)](https://imgse.com/i/v4gcLV)

## 第四步 安卓手机，连接到电脑相同的局域网
~~设置 -> 高级设置 -> 自定义同步服务器~~（此为老版配置地址,请使用文件夹内的安装包或者等待正式版`2.16`的发布，以此进入**设置-->同步-->自定义同步服务器**，设置同步地址和媒体文件同步地址。
[![xvy5cD.jpg](https://s1.ax1x.com/2022/11/07/xvy5cD.jpg)](https://imgse.com/i/xvy5cD)

## 一些额外话
为便于后续服务器软件打开，你可以将软件发送到开始菜单和桌面，这样你将能够通过开始菜单搜索找到我们的应用，
操作方法也很简单，在我们文件夹找到`send.exe`,双击它，允许管理员运行。
[![v4GqyR.png](https://s1.ax1x.com/2022/08/31/v4GqyR.png)](https://imgse.com/i/v4GqyR)

[![v4Gbl9.png](https://s1.ax1x.com/2022/08/31/v4Gbl9.png)](https://imgse.com/i/v4Gbl9)



### Ankidroid版本要求原因与版本选择
因为安卓安全性相关策略，较新的安卓系统会要求APP HTTPS连接，AnkiDroid 2.10-2.15.6都是基于这样设计的，在新版本2.16(目前为测试版)允许HTTP不安全连接，同样也降低了我们部署的难度和繁琐程度。

工具源来自 [anki-sync-server-rs](https://github.com/ankicommunity/anki-sync-server-rs)以及[anki-server-deploy](https://github.com/dobefore/anki-server-deploy)