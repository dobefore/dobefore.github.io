---
title: 在rust程序中调用c函数
readmore: true
date: 2023-01-04 11:45:41
tags: rust
---
## 需求
我想写一段rust程序，它能够接收到用户键盘输入就会立刻退出，即按任意键退出，但是不用用户敲击`enter`键。纯用rust写似乎不好实现，而利用现成的c语言却能很好地解决问题。

我们用c语言实现上面的功能，并在rust程序中调用c函数，我们把c静态编译成静态库，静态链接。

## 代码实现细节
我们使用构建库`cc`来编译c程序为静态库，利用rust构建脚本来搜索查找静态库。我们在main模块里面引入c库函数。

新建一个项目 `cargo new callc`.下面是各个文件的内容构成。

> src/press.c

c代码解释：`getch`函数从标准输入流读取一个字符，而不需要用户输入enter键，因为直接从键盘Buffer里面读取。一旦字符被读取，程序会退出。
注意`conio.h` 可能不是标准库函数，在除Windows以外的操作系统中可能会出现失败的情形。
```
#include <stdio.h>
#include <conio.h>

int press() {
    printf("Press any key to exit...\n");
    getch();
    return 0;
}
```

> Cargo.toml

```
build="build.rs"
[build-dependencies]
cc = "1.0.78"
```

> src/main.rs

声明我们要使用函数`press`
```
// Note the lack of the `#[link]` attribute. We’re delegating the responsibility
// of selecting what to link over to the build script rather than hard-coding
// it in the source file.
extern { fn press(); }

fn main() {
    unsafe { press(); }
}
```

> build.rs

编译`press.c`为静态库，紧接着在位置`OUT_DIR`环境变量所指示的目录下面找到静态库便于后面的链接。
```
use std::env;
fn main() {
    // out dir is in target/release/build
     let out_dir = env::var("OUT_DIR").unwrap();
    // Tell Cargo that if the given file changes, to rerun this build script.
    println!("cargo:rerun-if-changed=src/press.c");
    // Use the `cc` crate to build a C file and statically link it.
    cc::Build::new()
        .file("src/press.c")
        .compile("press");
            println!("cargo:rustc-link-search=native={}", out_dir);
    println!("cargo:rustc-link-lib=static=press");
}
```
## Reference
[1] https://doc.rust-lang.org/cargo/reference/build-script-examples.html