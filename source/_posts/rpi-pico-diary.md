---
title: raspberry pico观察日记
readmore: true
date: 2022-08-12 17:27:37
tags:
- raspberry-pico
- embeded
---
每次按住`bootsel`接入pc usb时，会擦除pico原来的程序（.uf2）;下载firmware到pico,第二次只是插入usb供电，不会擦除程序。

requirements (Installation of development dependencies):
- Toolchain support for the cortex-m0+ processors in the rp2040 (`thumbv6m-none-eabi`)
```
rustup target install thumbv6m-none-eabi
cargo install flip-link
# This is our suggested default 'runner'
cargo install probe-run
# If you want to use elf2uf2-rs instead of probe-run, instead do...
cargo install elf2uf2-rs --locked
```

run with `elf2uf2` (Loading a UF2 over USB)
Make sure your .cargo/config contains the following
```toml
[target.thumbv6m-none-eabi]
runner = "elf2uf2-rs -d"
```

connect pico to pc by pushing `bootsel` ,and then run `cargo run`