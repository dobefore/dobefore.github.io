---
title: rust_sciter_utf8_support
readmore: true
date: 2021-06-18 12:51:00
tags: 
- rust
- gui
- sciter
categories: program language
---

# Introduction

在用Rust运行sciter app 时，控件文字包含中文会出现乱码的问题。

# How to Fix

1. 如果在html页面里面，在 `<head>`标签里加上`meta` 标签注明字符集`utf-8`。

```html
  <head>
        <meta http-equiv="Content-Type" content="text/html; charset=utf-8"/>
    </head>
```

2. 如果是以BOM开始的utf8资源.

   ```
   first three bytes: EF BB BF). #不是太明白
   ```

   # reference

- [sciterloadhtml-and-utf-8](https://sciter.com/forums/topic/sciterloadhtml-and-utf-8/)

