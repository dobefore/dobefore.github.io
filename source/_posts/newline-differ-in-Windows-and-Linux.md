---
title: rust中的文本断行（newline）
date: 2021-06-09 19:27:43
tags: rust
categories: program language
readmore: true
---

## Introduction

在Windows平台用Rust编程，有时候需要写入batch（.bat）文件，但是却不能正确地执行。

下面是一个发送应用的快捷方式到桌面的batch。
<!-- more -->

```basic
@echo off
::设置程序或文件的完整路径（必选）
set Program=C:\Users\Admin\Desktop\anki_server.exe

::设置快捷方式名称（必选）
set LnkName=anki_server

::设置程序的工作路径，一般为程序主目录，此项若留空，脚本将自行分析路径
set WorkDir=

::设置快捷方式显示的说明（可选）
set Desc=测试

if not defined WorkDir call:GetWorkDir "%Program%"
(echo Set WshShell=CreateObject("WScript.Shell"^)
echo strDesKtop=WshShell.SpecialFolders("DesKtop"^)
echo Set oShellLink=WshShell.CreateShortcut(strDesKtop^&"\%LnkName%.lnk"^)
echo oShellLink.TargetPath="%Program%"
echo oShellLink.WorkingDirectory="%WorkDir%"
echo oShellLink.WindowStyle=1
echo oShellLink.Description="%Desc%"
echo oShellLink.Save)>makelnk.vbs
echo created shelllnk OK
makelnk.vbs
del /f /q makelnk.vbs
exit
goto :eof
:GetWorkDir
set WorkDir=%~dp1
set WorkDir=%WorkDir:~,-1%
goto :eof
```

执行后得到，'柟寮忓悕绉帮紙蹇呴€夛級' 不是内部或外部命令，也不是可运行的程序或批处理文件。

## Rust写文件默认的newline

### Windows中的体现

```rust
let p = "f.txt";
// 
    let mut file = OpenOptions::new()
        .create(true)
        .append(true)
        .open(p)
        .unwrap();

        writeln!(file,"a").unwrap();
        writeln!(file,"b").unwrap();
```

运行后，用记事本`f.txt`打开，显示如下：

![Linux_newline](https://z3.ax1x.com/2021/06/09/2cGvLD.png)](https://imgtu.com/i/2cGvLD)

结果看出是Unix风格的newline ""\n"，再看下Rust writeln!的文档说明：

> On all platforms, the newline is the LINE FEED character (`\n`/`U+000A`) alone (no additional CARRIAGE RETURN (`\r`/`U+000D`).

## 解决方式

Rust中为我们提供了macro  write!()，并没有newline。我们自己提供newline风格CRLE（\r\n）。

```
write!(file, "{}\r\n","c").unwrap();
```

