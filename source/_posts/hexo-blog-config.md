---
title: hexo-blog-config
readmore: true
date: 2022-05-16 08:48:18
tags:
- hexo
- blog
---

After clone blog source code into local,these steps should be done.

## install nodejs and npm

install archive file,unpack it.

```none
https://nodejs.org/en/download/
```



add bin path to .bashrc

```none
export PATH="$HOME/node-v16.14.2-linux-arm64/bin:$PATH"
```



## install theme -yun

if not,will cause

```none
WARN  No layout: about/index.html
WARN  No layout: tags/index.html
WARN  No layout: categories/index.html
```



[https://hexo-theme-yun.vercel.app/guide/#%E5%BF%AB%E9%80%9F%E5%BC%80%E5%A7%8B](https://hexo-theme-yun.vercel.app/guide/#快速开始)

## generate and deploy

```none
hexo g
hexo d
```