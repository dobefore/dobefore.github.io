---
title: gen-c-dynamical-library-using-rust-and-call
readmore: true
date: 2022-01-03 20:14:01
tags: 
- rust
- cdylib
---

### 使用rust生成动态库cdylib

#### layout

```
├── Cargo.lock
├── Cargo.toml
└── src
    └── lib.rs
```

#### Cargo.toml

```toml
[lib]
name = "rustdll" #生成dll的文件名
crate-type = ["cdylib"]
```

#### lib.rs

```rust
#[no_mangle]
pub extern fn gettime() {
    let input = 4;
  println!("from rust dll {}",input)
```

build之后，在Windows平台会生成两个文件 `rustdll.dll`可导入路``rustdll.dll.lib` ；而在Linux平台生成文件`librustdll.so`

### 调用由rust生成的动态库里的函数

#### layout

```
aa/
├── Cargo.lock
├── Cargo.toml
├── build.rs
├── lib
│   └── librustdll.so
└── src
    └── main.rs
```

#### LInux

build.rs

```rust
fn main() {
 // indicate dynamical library
    println!("cargo:rustc-link-lib=dylib=rustdll");
   // search lib directory,relative path is also ok
    println!("cargo:rustc-link-search=native=/home/ubuntu/aa/lib");
}
```

src/main.rs

```rust
和 build.rs 中的cargo:rustc-link-lib 二选一
//#[link(name = "rustdll")]
extern {
    fn gettime();
}
fn main() {
    unsafe {
        gettime();

    }
}
```

build command

if `cargo build`,可以编译但link error

```
 ldd target/debug/aa
        linux-vdso.so.1 (0x00007ffd5b12d000)
        librustdll.so => not found
```

add new flags

```
cargo rustc -- -C link-args="-Wl,-rpath,/home/ubuntu/aa/lib/"
```

#### Windows

src/main.rs

```rust
和 build.rs 中的cargo:rustc-link-lib 二选一
//#[link(name = "rustdll.dll")]
extern {
    fn gettime();
}
fn main() {
    unsafe {
        gettime();

    }
}
```

build.rs

```rust
fn main() {
    // search import library .lib
 // indicate dynamical library
    println!("cargo:rustc-link-lib=dylib=rustdll.dll");
   // search lib directory,relative path is also ok
    println!("cargo:rustc-link-search=native=..");
}
```

将`rustdll.dll`和`rustdll.dll.lib`放在和aa同目录下，执行`cargo build`

完成后，将可执行文件和动态库文件放在同一文件夹下即可

### Reference

[Linking Rust application with a dynamic library not in the runtime linker search path](http://ostack.cn/?qa=621344/)