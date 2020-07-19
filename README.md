# PasteAppLambda
The lambda functions required for the Paste Web app, which allows users to store tidbits, delete, and read them. Useful for log messages, and can allow for an automatic delete time.

See https://aws.amazon.com/blogs/opensource/rust-runtime-for-aws-lambda/ for instructions on how to build/compile function. Example given was used as base for the project.

## Pre-Installation
1. Cargo
2. Rustup
3. Homebrew

## Compliling on Mac
```
rustup target add x86_64-unknown-linux-musl
```

```
brew install filosottile/musl-cross/musl-cross
```

```
$ mkdir .cargo
$ echo '[target.x86_64-unknown-linux-musl]
linker = "x86_64-linux-musl-gcc"' > .cargo/config
$ ln -s /usr/local/bin/x86_64-linux-musl-gcc /usr/local/bin/musl-gcc
```

## Building the Function
```
cargo build --release --target x86_64-unknown-linux-musl
```

## Zipping the Function for Deployment
```
$ zip -j rust.zip ./target/x86_64-unknown-linux-musl/release/bootstrap
```
