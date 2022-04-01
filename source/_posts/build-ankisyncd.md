---
title: build_ankisyncd
readmore: true
date: 2021-11-06 13:17:10
tags:
- rust
- cross-compile
---

disable git verify ssl

```
export GIT_SSL_NO_VERIFY=true
```

### Configure  gcc

#### Install the C cross toolchain(only for armv7)

```
# Step 1: Install the C cross toolchain
$ sudo apt-get install -qq gcc-arm-linux-gnueabihf
```

#### add cargo compiled standard crates

```
#for aarch54
rustup target add aarch64-unknown-linux-musl
# for aarch32/armv7
rustup target add armv7-unknown-linux-musleabihf
#for darwin macos
rustup target add x86_64-apple-darwin
```

#### download cross-compile toolchains and set ENV var

1. aarch64/x86_64

enter site [https://musl.cc/](https://link.zhihu.com/?target=https%3A//musl.cc/)  to get musl-gcc and decompression

export bin (x86_64-linux-musl-native seems not able to build ,so use cross version)

```
export PATH="$HOME/aarch64-linux-musl-cross/bin:$PATH"
export PATH="$HOME/x86_64-linux-musl-cross/bin:$PATH"
source ~/.profile
```

2. armv7

   ```
   git clone --depth 1 https://github.com/raspberrypi/tools.git rpitools
   ```

   export bin

   ```
   export PATH="$HOME/rpitools/arm-bcm2708/arm-rpi-4.9.3-linux-gnueabihf/bin:$PATH"
   ```
3. macos
```
# Install build dependencies
sudo apt install \
    clang \
    gcc \
    g++ \
    zlib1g-dev \
    libmpc-dev \
    libmpfr-dev \
    libgmp-dev \
    libxml2-dev
```

Add the following to a script called osxcross_setup.sh and make it executable.
```
git clone https://github.com/tpoechtrager/osxcross
cd osxcross
wget -nc https://s3.dockerproject.org/darwin/v2/MacOSX10.10.sdk.tar.xz
mv MacOSX10.10.sdk.tar.xz tarballs/
UNATTENDED=yes OSX_VERSION_MIN=10.7 ./build.sh
```
run sh
```
./osxcross_setup.sh
```

Add to PATH ENV
```
export PATH="/home/ubuntu/osxcross/target/bin:$PATH"
```
   #### Configure Cargo

   cat ~/.cargo/config

   ```
   [target.x86_64-apple-darwin]
linker = "x86_64-apple-darwin14-clang"
ar = "x86_64-apple-darwin14-ar"

   [target.aarch64-unknown-linux-musl]
   linker = "aarch64-linux-musl-gcc"
   rustflags = ["-C", "target-feature=+crt-static", "-C", "link-arg=-lgcc"]
   
   [target.armv7-unknown-linux-musleabihf]
   linker = "arm-linux-musleabihf-gcc"
   rustflags  = [
       "-C", "target-feature=+crt-static",
       "-C", "link-args=-static",
   ]
   
   [target.x86_64-unknown-linux-musl]
   linker = "x86_64-linux-musl-gcc"
   rustflags = ["-C", "target-feature=+crt-static", "-C", "link-args=-static",]
   
   [net]
   retry = 2 # 失败 自动重试 次数
   git-fetch-with-cli = true
   ```

   

### Cross-compile openssl

#### cross-compile 

```
wget https://www.openssl.org/source/openssl-1.0.1t.tar.gz
tar -zxvf openssl-OpenSSL_1_1_1f
cd ..
# for aarch64
export MACHINE=aarch64
export ARCH=arm
export CC=aarch64-linux-musl-gcc
# for x86_64
export MACHINE=x86_64
export ARCH=x86_64
export CC=x86_64-linux-musl-gcc
#aarch32/armv7
export MACHINE=armv7
export ARCH=arm
# in rpitools
export CC=arm-linux-gnueabihf-gcc

cd openssl-OpenSSL_1_1_1f
# add --prefix=dir to apoint dir will be make install
./config shared && make
cd ..

# dont know if its true.fisrt time will build failed.change add OPENSSL_LIB_DIR # with lib,then build,this will fail and last change back and build 
export OPENSSL_LIB_DIR=/home/ubuntu/openssl-1.0.1t/
export OPENSSL_INCLUDE_DIR=/home/ubuntu/openssl-1.0.1t/include
export OPENSSL_STATIC=true

```
#### cross compile libsqlite3
this step isnt necessary during build ankisyncd,do in build
everydaytask.
```
export CC=aarch64-linux-musl-gcc
 ./configure --host=aarch64 --prefix=/home/ubuntu/sql

make & make install

  export SQLITE3_LIB_DIR=$HOME/sql/bin/
 export SQLITE3_INCLUDE_DIR=$HOME/sql/include/
```
### build ankisyncd

at last ,build

```
# aarch64
cargo build --target=aarch64-unknown-linux-musl --release

#aarch32/armv7
 cargo build --target armv7-unknown-linux-musleabihf --release
#linux x86_64
cargo build --release --target=x86_64-unknown-linux-musl
# MacOS x86_64
CC=o64-clang \
CXX=o64-clang++ \
SQLITE3_SYS_STATIC=1 \
OPENSSL_SYS_STATIC=1 \
cargo build --target x86_64-apple-darwin
```

package and compression

```
tar -czvf ankisyncd_linux_armv7.tar.gz ankisyncd ankisyncctl
```



### Reference

- [cross compile for armv7](https://jiapeng.me/helium-gateway-rs-compile/)
- [rust cross github](https://github.com/japaric/rust-cross)
- [交叉编译rust-openssl crate for armv7](https://www.cnblogs.com/sevenyuan/p/13663372.html)
- [How to build openssl-sys crate for musl in Rust](https://qiita.com/liubin/items/6c94f0b61f746c08b74c)
- [git错误error: server certificate verification failed. CAfile:](https://www.jianshu.com/p/7d599bdf370a)
- [MUSL 支持完全静态二进制文件](https://rustwiki.org/zh-CN/edition-guide/rust-2018/platform-and-target-support/musl-support-for-fully-static-binaries.html)
- [git-fetch-with-cli](https://doc.rust-lang.org/cargo/reference/config.html)