---
title: rust-fatal-error-link1201
readmore: true
date: 2021-10-11 17:50:24
categories: program language
tags: rust
---

on occationally,当我run `cargo build` using building tool msvc,error appears as follows:

```
note: LINK : fatal error LNK1201: error writing to program database'D:\software\vscode_project\anki_sync\anki-sync-server-rs\target\debug\build\futures-channel-29fccd2a64763c5c\build_script_build-29fccd2a64763c5c.pdb'; check for insufficient diskspace, invalid path, or insufficient privilege
```

after search the Internet,I find the solution. You can delete the file error info refers to,that is,in this situation,`D:\software\vscode_project\anki_sync\anki-sync-server-rs\target\debug\build\futures-channel-29fccd2a64763c5c\build_script_build-29fccd2a64763c5c.pdb`. Or you just can delete folder /target ,problems  solved.

### reference

- [fatal error LNK1201: error writing to program database - Visual Studio 2003](https://stackoverflow.com/questions/35662865/fatal-error-lnk1201-error-writing-to-program-database-visual-studio-2003)